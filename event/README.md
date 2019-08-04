# События в JavaScript

[Страница](https://damir-art.github.io/event/)<br />
[Репозиторий](https://github.com/damir-art/damir-art.github.io/tree/master/event)

Все события https://developer.mozilla.org/ru/docs/Web/Events<br />
Все API https://developer.mozilla.org/ru/docs/Web/API<br />
API Event https://developer.mozilla.org/ru/docs/Web/API/Event<br />
События мыши https://developer.mozilla.org/ru/docs/Web/API/MouseEvent

el.addEventListener('event', func) - добавляет событие

### При клике на кнопку, меняется надпись у заголовка
    var button = document.querySelector('button')
    var h1 = document.querySelector('h1')

    function buttonClick() {
        if (h1.textContent == 'Event in JavaScript') {
            h1.textContent = 'Button click!'
        } else {
            h1.textContent = 'Event in JavaScript'
        }

    }
    button.addEventListener('click', buttonClick)

### При изменении текстового поля, меняется надпись у заголовка
    var h1 = document.querySelector('h1')
    var input = document.querySelector('input')
    
    input.addEventListener('input', function () {
        h1.textContent = input.value
    })

### Используем ключевое слово this
    h1.addEventListener('mouseenter', function () {
       // h1.textContent = 'Mouseenter H1!'
       console.log(this);
       this.style.color = '#eee'
       this.style.backgroundColor = '#111'
    })
    h1.addEventListener('mouseleave', function () {
        // h1.textContent = 'Mouseleave H1!'
        console.log(this);
        this.style.color = '#111'
        // this.style.backgroundColor = "#eee"
    })

## Погружение и всплытие событий
    // При клике на id=2, клик по id=1 тоже сработает (погружение)
    <div class="box-1" id="1">
        <div class="box-2" id="2"></div>
    </div>
    
    var divs = document.querySelectorAll('div')
    for(var i = 0; i < divs.length; i++ ) {
        divs[i].addEventListener('click', function(){
            console.log(this.getAttribute('id')) // 2, 1
        })
    }
    
    // меняем порядок с 2, 1 на 1, 2 (всплытие)
    divs[i].addEventListener('click', function(){
        console.log(this.getAttribute('id')) // 2, 1, третий параметр true у addEventListener
    }, true)
    
# Объект событие (event)
Управляем или отменяем поведением по-умолчанию
* event
* event.target
* event.target.nodeName и т.д.
* event.stopPropagation()
* event.preventDefault()
* вместо this лучше использовать event.target

Отменяем погружение-всплытие:

    for(var i = 0; i < divs.length; i++ ) {
        divs[i].addEventListener('click', function(event){
            event.stopPropagation()
            console.log(this.getAttribute('id'))
        })
    }

Отменяем действие по умолчанию, например переход по ссылке:

    a.addEventListener('click', link_click)

    function link_click(event) {
        event.preventDefault()

        var div = divs[0]
        div.style.display = div.style.display === 'none'
            ? 'flex'
            : 'none'

        console.log(div.style.display)
    }

## Делегирование событий
Делегирование событий - это оптимизация, улучшение производительности кода JavaScript. Добавляем прослушку событий не на каждый элемент, а на их обёртку.
* getElementById() - самый быстрый метод при работе с DOM-деревом

Не оптимизированный код

    var ps = document.querySelectorAll('p')

    for(var i = 0; i < ps.length; i++ ) {
        ps[i].addEventListener('click', function(event){
            event.target.style.color = 'red'
        })
    }

Оптимизированный код

    // addEventListener висит только на одном объекте а не на множестве
    document.getElementById('wrapper').addEventListener('click', function () {
        var tagName = event.target.tagName.toLowerCase()

        // меняем цвет по имени тега
        if(tagName === 'p') {
            event.target.style.color = 'green'
        }
        console.log(tagName)

        // меняем цвет по имени класса
        if(event.target.classList.contains('class_name')) {
            event.target.style.color = 'orange'
        }
    })
