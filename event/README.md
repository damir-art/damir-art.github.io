# События в JavaScript

[Страница](https://damir-art.github.io/event/)<br />
[Репозиторий](https://github.com/damir-art/damir-art.github.io/tree/master/event)

Все события https://developer.mozilla.org/ru/docs/Web/Events<br />
Все API https://developer.mozilla.org/ru/docs/Web/API<br />
API Event https://developer.mozilla.org/ru/docs/Web/API/Event<br />
События мыши https://developer.mozilla.org/ru/docs/Web/API/MouseEvent

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
