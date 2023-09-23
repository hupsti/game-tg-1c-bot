# Шаблон телеграм-бота для обучения

## Системные требования

Бот разработан на платформе 1С:Предприятие версии 8.3.22.1750, в качестве IDE использована EDT 2022.2.3

Для работы бота и его доработки нужны эти версии или выше

## Начальный запуск

1. Скачать конфигурацию из файлов релиза
1. Создать новую информационную базу
1. Загрузить конфигурацию в информационную базу, запустить в пользовательском режиме
1. С помощью https://t.me/BotFather создать нового бота и поместить его токен в соответствующее поле на начальной странице
1. Выбрать режим работы бота и запустить
1. Написать первое сообщение боту

## Описание функций

### Взаимодействие с телеграм

Приложение осуществляет взаимодействие с Telegram через официальное [API для ботов](https://core.telegram.org/bots/api).

Для получения входящих сообщений используется метод Long polling, не требуется веб-публикации для работы.

Сообщения принимаются только при запущенном приложении и включенной обработке входящих сообщений.

Программный интерфейс позволяет:
1. Принимать текстовые сообщения
1. Обрабатывать нажатия интегрированной клавиатуры
1. Отправлять текстовые сообщения и фото (в т.ч. работать с клавиатурой)
1. Редактировать текстовые сообщения и подписи в фото (в т.ч. работать с клавиатурой)

### Эхо бот

В режим работы Эхо бот на все входящие сообщения отвечает сообщением с аналогичным текстом

### Простая викторина

Для работы режима необходимо предварительное заполнение справочника Вопросы простой викторины

При получении первого сообщения предлагает выбрать вопрос на клавиатуре в поле ввода

Каждый вопрос сопровождается вариантами ответа, пользователю дается одна попытка ответа

## Создание своих функций

Для создания своего режима работы бота необходимо:
1. Добавить режим работы бота в перечисление `РежимРаботыБота`
1. Создать свой общий модуль (можно скопировать `ТелеграмЭхо`)
1. В методе `ИнтеграцияТелеграмПереопределяемый.ПриОбработкеЭлементаОчереди` добавить обработку нового элемента перечисления с передачей управления в новый общий модуль
1. Реализовать в своем общем модуле небходимые функции, добавить необходимые объекты метаданных для работы алгоритма
1. Создать новую подсистему и включить в нее все добавленные объекты

При недостаточной функциональности методов взаимодействия с API оставляейте пожелания в https://github.com/matvey-seregin/game-tg-1c-bot/issues или самостоятельно реализуйте необходимую функциональность и направляйте Pull requests для включения новых функций в основную ветку.
 
 Созадетль: Клишин Марк