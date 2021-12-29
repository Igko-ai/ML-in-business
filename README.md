# python-flask-docker
Итоговый проект курса "Машинное обучение в бизнесе"

Стек:

ML: catboost, sklearn, pandas, numpy
API: flask
Данные: https://archive.ics.uci.edu/ml/datasets/Adult

Задача: предсказать заработок. Бинарная классификация

Обзор данных:

Целевая переменная:
target (заработок): >50K, <=50K.

Признаки:
age (возраст)
workclass (рабочий статус): Private, Self-emp-not-inc, Self-emp-inc, Federal-gov, Local-gov, State-gov, Without-pay, Never-worked.
fnlwgt (примерная оценка количества людей с такими же характеристиками)
education (уровень образования): Bachelors, Some-college, 11th, HS-grad, Prof-school, Assoc-acdm, Assoc-voc, 9th, 7th-8th, 12th, Masters, 1st-4th, 10th, Doctorate, 5th-6th, Preschool.
educational-num (длительность обучения)
marital-status (семейное положение): Married-civ-spouse, Divorced, Never-married, Separated, Widowed, Married-spouse-absent, Married-AF-spouse.
occupation (поле деятельности): Tech-support, Craft-repair, Other-service, Sales, Exec-managerial, Prof-specialty, Handlers-cleaners, Machine-op-inspct, Adm-clerical, Farming-fishing, Transport-moving, Priv-house-serv, Protective-serv, Armed-Forces.
relationship (положение в семье): Wife, Own-child, Husband, Not-in-family, Other-relative, Unmarried.
race (раса): White, Asian-Pac-Islander, Amer-Indian-Eskimo, Other, Black.
sex (пол): Female, Male.
capital-gain (прирост капитала).
capital-loss (потеря капитала).
hours-per-week (количество рабочих часов в неделю).
native-country (страна рождения): United-States, Cambodia, England, Puerto-Rico, Canada, Germany, Outlying-US(Guam-USVI-etc), India, Japan, Greece, South, China, Cuba, Iran, Honduras, Philippines, Italy, Poland, Jamaica, Vietnam, Mexico, Portugal, Ireland, France, Dominican-Republic, Laos, Ecuador, Taiwan, Haiti, Columbia, Hungary, Guatemala, Nicaragua, Scotland, Thailand, Yugoslavia, El-Salvador, Trinadad&Tobago, Peru, Hong, Holand-Netherlands.

Используемые признаки:

- age (int)
- capital-gain (int)
- hours-per-week (int)

Модель для отбора признаков: catboost

Модель классификации: logreg

### Клонируем репозиторий и создаем образ
```
$ git clone https://github.com/fimochka-sudo/GB_docker_flask_example.git
$ cd GB_docker_flask_example
$ docker build -t fimochka/gb_docker_flask_example .
```

### Запускаем контейнер

Здесь Вам нужно создать каталог локально и сохранить туда предобученную модель logreg.dill (<your_local_path_to_pretrained_models> нужно заменить на полный путь к этому каталогу)
```
$ docker run -d -p 8180:8180 -p 8181:8181 -v <your_local_path_to_pretrained_models>:/app/app/models fimochka/gb_docker_flask_example
```

### Переходим на localhost:8181
