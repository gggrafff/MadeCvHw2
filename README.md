# MadeCvHw2
Второе домашнее задание по CV. MADE набор 2019.  
Поиск автомобильных номеров на изображениях и распознавание текста номеров.  

## Что сделал и чего не делал?  
В этом задании я попробовал совсем немного, скорее просто прощупал почву. Не хотелось делать сложное, объёмное ресурсоёмкое решение, хотелось обойтись малым объёмом вычислений (очень впечатлили некоторые решения ребят в первом дз, которые попали в топ, не производя огромных вычислений).  
За основу брал код с семинара, на котором рассматривалась эта задача.  

Первое, что попробовал - это Mask R-CNN на основе ResNet50 + CRNN на основе ResNet18 и GRU. Это дало скор 1.69616 на private. Оно же в лидерборде осталось в качестве финального решения.  
Пробовал заменить ResNet18 на более объёмную densenet121. Код обучения оставил прежний, качество упало. Думаю, если с толком подойти к процессу обучения, то можно было получить положительное улучшение. Использование двунаправленной gru давало незначительные изменения скора в данной ситуации. Но думаю, что если бы свёрточная часть работала качественнее, то эффект от двунаправленного rnn был бы значительнее.  
Посмотрел сгенерированные номера. Попробовал использовать их с минимальным изменением кода обучения модели. Обучал сначала на них пару эпох, потом дообучал на настоящих данных. Качество упало. Думаю, нужно очень аккуратно использовать сгенерированные номера и написать ряд аугментаций, чтобы превратить сгенерированные картинки во что-то похожее на реальные изображения.  

Что не попробовал?  
* Почистить датасет.  
* Попробовать для выделения номеров что-то кроме maskrcnn.  
* Использовать аугментации для сгенерированных изображений.  

## Результат  
Итого, 1.69616 на private leaderboard с Mask R-CNN на основе ResNet50 + CRNN на основе ResNet18 и GRU.  
