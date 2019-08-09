# Разное о JavaScript

## Атрибуты тега script: `async` и `defer`
Специальные атрибуты тега `<script>`. У данных атрибутов нет значений.

    <script async ...
    <script defer ...

`async` &ndash; браузер не будет ждать окончания загрузки скрипта и продолжит загружать следующий код. Обычно такой атрибут используют если помещают теги `script` в `head`.
`defer` &ndash; тоже самое что и `async` только, если `defer` на странице будет несколько то последние не загрузятся до тех пор пока не прогрузятся первые `defer`.

## Модальные окна в JavaScript

### alert()

    // alert()
    document.querySelector('#alert').addEventListener('click', function () {
        alert('Hello')
    })
    
### confirm()

    // confirm()
    document.querySelector('#confirm').addEventListener('click', function () {
        var decision = confirm('OK or CANCEL?')
    
        console.log(decision)

        if (decision) {
            console.log('OK')
        } else {
            console.log('CANCEL')
        }
    })

### prompt()

    // prompt()
    document.querySelector('#prompt').addEventListener('click', function () {
        // Сохраняем в переменную, строковое значение введённое пользователем
        var color = prompt('Введите цвет:', 'Значение по-умолчанию...')

        console.log(color)

        if (color === 'Белый') {
            console.log('Вы ввели белый')
        } else {
            console.log('Вы ввели не белый')
        }
    })

### Вывод ошибок

    // выводит ошибку
    throw new Error('Выводим ошибку!') // останавливает выполнение кода

### console...

    // console...
    console.log('Выводим лог программы!')
    console.warn('Выводим предупреждение!')
    console.info('Выводим информацию!')
    console.error('Выводим ошибку!')

