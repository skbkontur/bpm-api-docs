Формирование PATCH запросов
===========================

Для изменения значений полей сущностей используется HTTP-метод PATCH 
с contntent/type application/json-patch+json описывающем изменение полей сущности. Рассмотрим пример:

Исходный объект в API:

.. code-block::

    {
        "name": "Наименование чего-либо",
        "creationTime" : "2021-06-05T21:56:43.000+00:00",
        "comment" : "Какой-то комментарий"
    }

Для модификации сущности необходимо отправить 
HTTP-запрос PATCH с content-type application/json и телом запроса:

.. code-block::

    {
        "operations": [
            { "op": "Replace", "path": "/comment", "Новый комментарий"},
            { "op": "Replace", "path": "/name", "Нормальное наименование"}
        ]
    }

Результат:

.. code-block::

    {
    "name": "Нормальное наименование",
    "creationTime" : "2021-06-05T21:56:43.000+00:00",
    "comment" : "Новый комментарий"
    }
    
Все операции будут применены в описанном порядке. Если в результате применения будет 
ошибка или она возникнет при валидации/сохранении результирующего объекта 
— не примениться ни одна из операций, API вернет сообщение об ошибке.