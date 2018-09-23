# ods_wiki
Выжимка полезных моментов из обсуждений в ods.ai

## Интервью

[Сергей Мушинский - "Мне 30, а я в Ангарске"](https://dev.by/news/angarsk-minsk)

[Evgeny Patekha - "My story: how to start a data scientist career with Kaggle?"](https://www.youtube.com/watch?v=X3ljF4kAQ8Y)

[Не только интервью, но целый канал тренировок по ML](https://www.youtube.com/channel/UCeq6ZIlvC9SVsfhfKnSvM9w)

[Валерий Бабушкин - "Как стать боссом"](https://www.youtube.com/watch?v=HuAjBrjWfYI)

## Рекомендации курсов
### Математическая база

### Python
[Stepic, "Программирование на Python"](https://stepik.org/course/67/)

### Machine Learning

### Deep Learning
[fast.ai: быстро практика, а потом уже теория.](http://course.fast.ai/)

[CS231n Stanford](http://cs231n.stanford.edu/)

[Специализация deeplearning.ai от Andrew Ng](https://www.coursera.org/specializations/deep-learning)

[Видео-лекции от sim0nsays](https://www.youtube.com/channel/UCQj_dwbIydi588xrfjWSL5g)

## Технические инструкции
### Удалённое подключение к девбоксу ([Slack](https://opendatascience.slack.com/archives/C1XP769LY/p1537560766000100))
0. Убедиться, что на компе белый айпи, в идеале статичный, иначе настроить dyndns или что там сейчас не знаю, обычно роутеры что-то свое поддерживают
1. На роутере добавить port forwarding 22-го порта во внутренний адрес твоей домашней тачки
2. На ней же поставить `openssh-server`
3. На клиенте (с той, с к которой подключаешься), скопировать `.ssh/id_rsa.pub`
4. Добавить его в `.ssh/authorized_keys` на тачке-сервере
5. Подключаться по ip или адресу
5.1. Настроить `.ssh/config` с чем-нибудь навроде
```Host kompdoma
    hostname 4.8.14.16
    user vasyan```
Подключаешься потом как `ssh kompdoma`
