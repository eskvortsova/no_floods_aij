# Прогноз уровня воды в реке Амур

В решении для показаний каждого гидропоста строится отдельная модель временного ряда.

Для прогнозирования временных рядов использована библиотека `Catboost`. Для того, чтобы предать модели больше данных и не сбрасывать строки, в которых есть пропуски, мы использовали модель
DecisionTreeRegressor. Каждый признак, в котором есть пропуски, заполнялся прогнозными значениями, общим контекстом для которого использовались все оставшиеся признаки, пропуски в которых
были заполнены медианными значениями.


### Прогноз погоды

Для прогнозирования уровня воды нужен прогноз метеоданных, в предложенном решении используются исторические данные, предоставленные организаторами.

### Возможности улучшения качества прогноза

* Использование более сложных моделей на основах деревьев и бустинга для восполнения пропусков
* Изменение исходной обработки данных: восполнение пропусков, explode КСВД
* Использование фаз луны для прогнозирования, в качестве гипотезы о приливах и отливах мировых вод
* Использование дополнительных параметров: водопроницаемость и насыщенность воздухом почыы, учет корневых систем деревьев местности