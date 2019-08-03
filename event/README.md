# События в JavaScript

[Страница](https://damir-art.github.io/event/)<br />
[Репозиторий](https://github.com/damir-art/damir-art.github.io/tree/master/event)

При клике на кнопку, меняется надпись у заголовка:

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
