Маршрут
==========

Маршрут — это набор состояний (узлов — nodes), которые проходит документ. 
В каждом узле пользователи совершают действия: согласуют, подписывают или ознакамливаются с документом.

Аргументы маршрута:

* Название
* Идентификатор
* Набор узлов маршрута
* Стартовый узел
* Идентификатор сущности в пачке — чтобы при массовых операциях можно было поматчить ответ с запросом

Узел — конкретное состояние и содержит в себе такие свойства:

* Название
* Идентификатор
* Ссылка на тип задачи
* Список узлов, в которые можно перейти

.. code-block::

    object {
    name: string
    externalId: string
    nodes: array of objects [
        object {
        id: string <uuid>
        name: string
        taskType: string
        nextNodeIds: array of strings [
            string <uuid>
            ]
        }
    ]
    startNodeId: string <uuid>
    batchItemKey: string 
    }
