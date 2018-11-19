### Разметка датасетов
#### Где нанять исполнителей за небольшие деньги
[Яндекс.Толока](https://toloka.yandex.ru/)

[Amazon Mechanical Turk](https://www.mturk.com/)

#### Как организовать разметку картинок/видео самостоятельно
|Инструмент|Картинки|Видео|Комментарии|
| ---- | ---- | ---- | ---- |
|[labelImg](https://github.com/tzutalin/labelImg)|||Веб-интерфейса нет, ставится как приложение.|
|[supervise.ly]()|||      |
|[cvat](https://github.com/opencv/cvat)|+|+|**movchan74**:  CVAT имеет перегруженный интерфейс, xml (json в scalabel), но разметка работает хорошо. |
|[scalabel](https://github.com/ucbdrive/scalabel)||| **movchan74**: Интерфейс у  Scalabel лучше, но имеет проблемы с удобством расстановки боксов: очень сложно изменить, т.к. он делает новый бокс если немного промахнулся, а бокс до самого края вообще не делается, надо потом исправлять. У них даже в демо видео эти проблемы видны https://www.youtube.com/watch?v=eiqy9uTpKQo&feature=youtu.be |

Обсуждение [тут](https://opendatascience.slack.com/archives/C047H3DP4/p1537784622000100)

### Отслеживание прогресса выполнения кода
1. Сообщения из кода в telegram через [telegram-send](https://habr.com/post/339682/).
2. tqdm
3. [tqdm в Telegram](https://github.com/ermakovpetr/tg_tqdm)
4. [telegram callback для Keras](https://github.com/qubvel/keras_telegram_callback)

### SOTA в NLP
https://nlpprogress.com/
