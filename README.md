# factRuEval-2016
http://www.dialog-21.ru/evaluation/2016/letter/

----

###Форма регистрации участников
http://goo.gl/forms/DLqEVW4NLf

После регистрации вы получите кодовое имя и ссылку на тестовую коллекцию.


###Форма регистраци прогонов
http://goo.gl/forms/snXO6MeHDo

После обработки архива вы получите подтверждение того, что он зарегистрирован оргкомитетом.


Все подтверждения высылаются вручную, т.е. они придут не сразу.


###Даты

* до 23:00 26.02.2016 - регистрация прогонов
* до 29.02.2016 - предварительные оценки
* 29.02.2016 - публикация разметки тестсета (в этом репозитории)
* до 01.03.2016 (включительно) - подача статей на конференцию Диалог (статьи нужно отправлять сюда: Secretary@dialog-21.ru)
* до 23:00 04.03.2016 - принимаются сообщения об ошибках в тестсете
* до 10.03.2016 - окончательне оценки (с учётом найденных ошибок)

----

* scripts/
    * t1_eval.py - компаратор для первой дорожки
    * Readme.txt - инструкция к компаратору
  
* devset/ - демонстрационная коллекция
    * *.txt      - тексты документов
    * *.tokens   - деление на токены и предложения
    * *.spans    - спаны (первый слой разметки)
    * *.objects  - упоминания объектов (второй слой разметки)
    * *.coref    - кореференция и идентификация (третий слой разметки)

 Описание модели разметки: http://opencorpora.org/wiki/Nermanual/2/model

## Формат демонстрационной разметки

### Тексты документов (*.txt)
Текст предложений сохранён из источника. Предложения склеены через пробел. Абзацы - через двойной перевод строки.

### Сегментация на токены и предложения (*.tokens)
Каждая строка - один токен. Предложения разделены пустой строкой.

Описание одного токена состоит из следующих полей:
- id токена
- позиция начала токена (от начала текста)
- длина токена
- текст токена
 
Разделитель полей - пробел. В токене пробела быть не может.

### Спаны (*.spans)
Каждая строка - один спан. Разделитель полей - пробел.

Поля:
- тип спана
- id спана
- позиция начала спана (от начала текста)
- длина в символах
- первый токен спана
- длина в токенах

Справочно (после решётки):
- все id входящих токенов
- все тексты входящих в спан токенов

### Упоминания объектов (*.objects)
Каждая строка - одно упоминание объекта. Разедлитель полей - пробел.

Поля:
- id упоминания
- тип упоминания
- список идентификаторов входящих в упоминание спанов

Справочно (после решётки):
- текст всех входящих в упоминание объекта спанов

### Кореференция и идентификация (*.coref)
Каждая запись - один объект. Разделитель записей - пустая строка.

Первая строка записи состоит из следующих полей:
- идентификатор объединённого объекта
- список идентификаторов упоминаний объектов, входящих в объединённый объект

Последующий строки:
- ключ
- значение

Допустимые ключи:
- firstname, surname, patronymic, nickname - у объектов типа Person
- name - у Location, LocOrg, Org
- wikidata - у всех
