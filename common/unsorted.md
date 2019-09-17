### Разметка датасетов
#### Где нанять исполнителей за небольшие деньги
[Яндекс.Толока](https://toloka.yandex.ru/)

[Amazon Mechanical Turk](https://www.mturk.com/)

#### Как организовать разметку картинок/видео самостоятельно
|Инструмент|Текст|Картинки|Видео|Комментарии|
| ---- | ---- | ---- | ---- | ---- |
|[labelImg](https://github.com/tzutalin/labelImg)||||Веб-интерфейса нет, ставится как приложение.|
|[supervise.ly]()||+||[Описание возможностей](https://hackernoon.com/%EF%B8%8F-advanced-annotation-tools-in-deep-learning-training-data-for-computer-vision-with-supervisely-847f8699a9cb), [Возможности в связке с YOLOv3](https://medium.com/@deepsystems/human-in-the-loop-for-object-detection-with-supervisely-and-yolo-v3-fa205ff07c1f)|
|[cvat](https://github.com/opencv/cvat)||+|+|**movchan74**:  CVAT имеет перегруженный интерфейс, xml (json в scalabel), но разметка работает хорошо. |
|[scalabel](https://github.com/ucbdrive/scalabel)|||| **movchan74**: Интерфейс у  Scalabel лучше, но имеет проблемы с удобством расстановки боксов: очень сложно изменить, т.к. он делает новый бокс если немного промахнулся, а бокс до самого края вообще не делается, надо потом исправлять. У них даже в демо видео эти проблемы видны https://www.youtube.com/watch?v=eiqy9uTpKQo&feature=youtu.be |
|[prodi.gy](https://prodi.gy/features/named-entity-recognition)|+||| NER, Text Classification. 3 уровня платных лицензий. |
|[brat](http://brat.nlplab.org/)|+|-|-| NER |
|[doccano](https://github.com/chakki-works/doccano)|+|-|-|doccano is an open source text annotation tool for human. It provides annotation features for text classification, sequence labeling and sequence to sequence. So, you can create labeled data for sentiment analysis, named entity recognition, text summarization and so on. Just create project, upload data and start annotation. You can build dataset in hours.|
|[labelme](https://github.com/wkentaro/labelme)|-|+|+|Умеет экспортировать даратесы в форматах VOC и COCO|

Обсуждение [тут](https://opendatascience.slack.com/archives/C047H3DP4/p1537784622000100)

#### Статьи Романа Куцева из http://trainingdata.ru/
"Мы делим задачи на разметку данных на два типа:
1. Ту, которую можно отдать на краудсорсинг в толоку или mturk. Обычно это задачи бинарной классификации, либо на Image Labeling. Плюсы: очень дешево, быстро можно разметить огромный объем данных, хорошее качество разметки (если установлены перекрытия и настроены ханипоты). Минусы: на подготовку задания уходит где-то пол дня, проблемы с разметкой персональных данных, можно разметить только простые задания.  Летом я написал довольно большую статью об этом. https://habr.com/company/ods/blog/358574/
2. Ту, которую мы не можем отдать на краудсорсинг в толоку. А именно сегментацию, маттинг, а также сложные задания, где надо долго учить фрилансеров. Плюсы: офигенное качество разметки, можно делать очень сложную разметку, все в порядке с персональными данными. Минусы: дороже, довольно долго, нужен специальный менеджер, который будет следить за фрилансерами. По такому типу разметки я тоже написал статью, вот: https://habr.com/post/422999/ . Код для проверки разметки есть в этой статье. Сложную разметку делаем в фотошопе либо в специальных плагинах для фотошопа."
(с) [Slack](https://opendatascience.slack.com/archives/CDSG994UQ/p1542738098125000?thread_ts=1542542717.089900&cid=CDSG994UQ)

### Отслеживание прогресса выполнения кода
1. Сообщения из кода в telegram через [telegram-send](https://habr.com/post/339682/).
2. tqdm
3. [tqdm в Telegram](https://github.com/ermakovpetr/tg_tqdm)
4. [telegram callback для Keras](https://github.com/qubvel/keras_telegram_callback)

### SOTA в NLP
https://nlpprogress.com/

### Эффективные реализации KNN на больших объёмах
#### faiss
* может обрабатывать огромные объемы данных (миллиарды точек)
* высокая скорость ответа на GPU
* точность индексов средняя
* есть неожиданные баги, так что не совсем production ready
Вывод: когда данных очень много - это единственный вариант, если нет - то не стоит использовать

#### annoy
* может обрабатывать большие объемы данных (сотни миллионов)
* скорость ответа хороша и можно мапить индекс в память, чтобы легко скейлить на кластерах
* точность индексов выше среднего
* также есть баги, но не в таком количестве, как у faiss
Вывод: лучшее решение для продакшена, когда данные умещаются в оперативку

#### nmslib
* может обрабатывать средние объемы данных (десятки миллионов)
* есть настраиваемый batch-query
* точность лучшая на рынке
* багов не замечал, но тоже есть
Вывод: лучшее решение для мини-демок, когда данных мало, а вау-эффекта хочется

Остальные либы подходят только для специфических кейсов. Например, если данных совсем мало, порядка десятка тысяч, то тут вообще лучшим будет sklearn.neighbors с KDTree.
