# Домашнее задание к занятию 3.2 Параметры и возвращаемое значение

Форум рос и процветал. Заказчику потребовались возможности более тонкого управления приложением.

## Задача № 1

Напишите функцию, которая умеет возвращать посчитанную репутацию пользователя по формуле: разница лайков и дизлайков, которые ставят другие пользователи, умноженная на коэффициент. Коэффициент представляет из себя долю не отредактированных сообщений пользователя. Если дизлайков больше, чем лайков, то коэффициент не применяется. Если сообщений у пользователя нет, его репутация равна 0.

### Процесс реализации
1. Объявите функцию с параметрами: количество лайков, дизлайков, количество отредактированных сообщений и общее количество сообщений.
2. Посчитайте репутацию по формуле.
3. Верните значение из функции.
4. Вызовите функцию с различными значениями, напечатайте значение и убедитесь, что репутация считается верно.

## Задача № 2

Форумы содержат много тем для обсуждения, и нам часто приходится печатать по несколько сообщений из каждой темы. В одной книге вы прочитали, что такие частые операции нужно выделять в функции, и решили выделить печать ленты сообщений в теме в отдельную функцию.

На вход функция принимает объект темы `thread`, а также количество сообщений для печати. 

Тестовый объект `thread`:
```js
let thread = {
    title: "Поделитесь книжкой",
    author: "RuBrick",
    total: 23,
    messages: [
        {
            id: 13201,
            date: "2018-01-09",
            text: "Посоветуйте, пожалуйста, с одной стороны подробную, а с другой доступную для понимания книгу по javascript. Спасибо",
            author: {
              name: "RuBrick",
              login: "ru_brick",
              reputation: 3,
              role: "user"
            }
        },
        {
            id: 13208,
            date: "2018-01-12",
            text: "Неужели нет хорошей литературы?",
            author: {
              name: "RuBrick",
              login: "ru_brick",
              reputation: 3,
              role: "user"
            }
        },
        {
            id: 13209,
            date: "2018-01-12",
            text: "в общем, NodeJS это JS + некоторые доп. модули и объекты. Тебе нужна литература по самому JS и дока на официальном сайте.",
            author: {
              name: "Popov",
              login: "popov_ma",
              reputation: 2310,
              role: "user"
            }
        },
        {
            id: 13219,
            date: "2018-01-14",
            text: "В сети много сайтов с хорошими объяснениями + есть курсы.",
            author: {
              name: "Void",
              login: "void",
              reputation: 5005,
              role: "user"
            }
        },
        {
            id: 13220,
            date: "2018-01-14",
            text: "Есть большая книга «JavaScript.Подробное руководство», потом смотришь документацию.",
            author: {
              name: "noname",
              login: "noname",
              reputation: 100,
              role: "user"
            }
        },
        {
            id: 13250,
            date: "2018-01-19",
            text: "Или можно посмотреть видео-курсы на youtube! А самое главное - практика! И этот форум - лучшая тренировочная площадка!",
            author: {
              name: "noname",
              login: "noname",
              reputation: 110,
              role: "user"
            }
        },
        {
            id: 13259,
            date: "2018-01-20",
            text: "Понял, спасибо!",
            author: {
              name: "RuBrick",
              login: "ru_brick",
              reputation: 13,
              role: "user"
            }
        }
    ]
};
```

### Процесс реализации
1. Объявите функцию с нужным количеством параметров.
2. Выводите на печать заданное количество сообщений в этой теме. Если количество сообщений, которых нужно напечатать, меньше, чем всего сообщений, то выбираем самые новые сообщения (т.е. если нужно напечатать 5 сообщений, а всего в теме 10 сообщений, то нужно выбрать 5 самых свежих). Шаблон для печати:
```
Автор1 (репутация: 5): текст сообщения
Автор2 (репутация: 10): текст сообщений
```
3. Если сообщений в теме нет, напечатайте текст «Ошибка формата! В теме нет сообщений».
4. Убедитесь, что функция работает корректно.

## Задача № 3

В каждом сообщении мы решили хранить информацию о том, редактировалось оно или нет. Для этого мы используем ключ `edited` и устанавливаем его в `true`, если сообщение отредактировано, и в `false` — в противном случае. Нужно написать функцию, которая по списку сообщений возвращала бы статистику — сколько сообщений из списка отредактировано, сколько нет и общее число сообщений в списке.

Тестовый массив `allMessages`:
```js
let allMessages = [
    {author: "zloy-zloy", text: "А у кого какой мобильный??", edited: true},
    {author: "zloy-zloy", text: "Я с андроидом. Уже 3 года живет, он самым крепким оказался, пережил 2 утопления.", edited: false},
    {author: "МамаЗузу", text: "Айфон в свое время успешно сдох при первом же падении на кафельную плитку.", edited: false},
    {author: "void", text: "У меня андроид. Особенно нравится, что никаких заморочек с айтюнс.", edited: false},
    {author: "mama", text: "Айфон.", edited: false},
    {author: "mama", text: "Почему не отвечаешь?", edited: false},
    {author: "void", text: "Дэвид Хэрман «Сила JavaScript. 68 способов эффективного использования JS».", edited: false},
    {author: "void", text: "Marijn Haverbeke, Вячеслав Голованов «Выразительный javascript: Введение».", edited: false},
    {author: "void", text: "Ленюсь.", edited: false},
    {author: "void", text: "Пока оценивать нечего.", edited: false},
    {author: "void", text: "Не по-русски как-то получается, хоть и на русском.", edited: false},
    {author: "ivanov", text: "Чип и Дейл прикольно, играл в детстве.", edited: false},
    {author: "ivanov", text: "hello, world", edited: true},
    {author: "void", text: "Сейчас напишу книгу по JS.", edited: false},
    {author: "ivanov", text: "Спасибо.", edited: false},
    {author: "ivanov", text: "Смысл такого видео? Все непонятные функции приходится самому смотреть. Надо не так делать. Пишете код - объясняете сразу, что к чему, голосом, ну, или там, текстом хотя бы, хотя лучше голосом.", edited: true},
    {author: "void", text: "Поделитесь видео-каналами по js.", edited: false},
    {author: "void", text: "Ничего не понравилось.", edited: false}
];
```

### Процесс реализации
1. Создайте функцию принимающую на вход список сообщений.
2. Посчитайте общее количество сообщений, количество отредактированных и неотредактированных сообщений.
3. Верните рассчитанные данные из функции.

***

## Инструкция по выполнению домашнего задания

1. Зарегистрируйтесь на сайте [Repl.IT](http://repl.it/).
2. Перейдите в раздел **my repls**.
3. Нажмите кнопку **Start coding now!**, если приступаете впервые, или **New Repl**, если у вас уже есть работы.
4. В списке языков выберите `JavaScript / Nodejs`.
5. Код пишите в левой части окна.
6. Посмотреть результат выполнения файла можно, нажав на кнопку **Run**. Результат появится в правой части окна.
7. После окончания работы скопируйте ссылку на ваш repl в адресной строке браузера.
8. В личном кабинете на сайте [netology.ru](http://netology.ru/) в поле комментария к домашней работе вставьте скопированную ссылку и отправьте работу на проверку.

При выполнении задания придерживайтесь [правил оформления кода на JavaScript](/codestyle.md).

*Никаких файлов прикреплять не нужно.*

Все задачи обязательны к выполнению для получения зачета. Присылать на проверку можно каждую задачу по отдельности или все задачи вместе. Во время проверки по частям ваша домашняя работа будет со статусом "На доработке".

Любые вопросы по решению задач задавайте в чате учебной группы.
