# **Translater for A2 students** README

This extension is designed for convenient text translation as an assistant to an unfortunate student with A2 ＼(◎o◎)／

## Work process

1. Выделение требующей перевода строки кода
2. Инициализация расширения путем сочетания быстрых клавиш `ctrl+shift+/`
3. Выбор языка на который требуется перевести текст в сплывающем окне:
 
![](images/Выбор_языка.png)

4. Сообщение о успешном выполнении перевода и изменение текста на идентичный в нужном языке

![](images/Перевод_успешен.png)

4. При наличии ошибки она будет выведена в всплывающем окне. В DebugConsole появится текст для перевода, исходный целивой язык и текст ошибки

![](images/окно_ошибки.png)

![](images/дебаг.png)

## Features
### translateCommand

- **Системное название команды:** `translate-this-text->_<`
- **Вызывное название команды:**  `Translate Selected Text`
- **Требует:** активный редактор
- **Получает на вход:** выделение текст в редакторе
- **Работа команды:**
1. Получаем текст из выделения и убираем лишние пробелы. Если текст не выделен, показывается сообщение и выполнение заканчивается.
2. Пользователю предлагается выбрать целевой язык для перевода. Это делается с помощью  `showQuickPick`
3. Исходный язык определяется на основе выбранного целевого языка. Если целью был выбран английский, значит исходный — русский, и наоборот.
4. Внутри блока  `try` мы отправляем `GET-запрос к API MyMemory`. 
    Запрос включает:
    - `q`: текст, который нужно перевести.
    - `langpair`: сочетание исходного и целевого языков.
5. Получения ответа от API и извлечение нужного текста.
6. Змена выделенный текст в редакторе на переведённый текст.
- **По завершении перевода:**
            - При успешном переводе отоброжается уведомление об успехе.
            - При возникновении ошибки, она обрабатывается в блоке `catch`. Сообщение об ошибке выводится в консоль и отображается пользователю.

- **Пример работы:**
Входная строчка: *Hi, I am a student at ITMO University*
Выходная строчка: *Привет, я студент Университета ИТМО*


### 1.0.0

Initial release of ...



## Автор
Акулиничева Мария Андреевна, M3100 # itmo-ISRPO
