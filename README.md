# URFU_ML_PI, group 2.11
## students: Sheshin N.A., Ivanov S.A., Perevispa O.V., Ovchar E.A.

## Перевиспа О.В. 
### Задание 1: Выбор модели предобученной модели МО и реализация скрипта
Выбран тип модели question-answering, модель timpal0l/mdeberta-v3-base-squad2. 
Пример работы модели [в скрипте qa.py](https://github.com/nasheshin01/URFU_ML_PI/blob/master/qa.py)

### Задание 2: Создание web-приложения МО на локальном компьютере
Ранее выбранная модель перенесена в приложение streamlit. Скриншоты работы приложения в scshots. Скрипт с приложением на streamlit [в файле qa_stlit.py](https://github.com/nasheshin01/URFU_ML_PI/blob/master/qa_stlit.py)

### Задание 3: Создание API-интерфейса для модели МО на локальном компьютере
Ранее выбранная модель пренесена в скрипт qa_fapi.py для работы с моделью через запросы API. Реализовано:
- метод GET на главную страницу, который возвращает просто текст, 
- метод POST по адресу /predict/ отрабатывает модель МО
- метод POST по адресу /sqnum/ возвращается квадрат переданного числа. 
Несколько методов созданы для тестирования функционала автоматического создания документация FastAPI. Скриншоты работы в scshots (в том числе скриншот cгенерированной документации). Реализация работы модели через запросы API [в файле qa_fapi.py](https://github.com/nasheshin01/URFU_ML_PI/blob/master/qa_fapi.py)

### Задание 4: Развертывание API-интерфейса модели в облаке Yandex.Cloud
- Модель развернута в облаке Яндекс клауд на [http://158.160.48.28:8000](http://158.160.48.28:8000).
- С API-документацией можно ознакомиться по ссылке [http://158.160.48.28:8000/docs](http://158.160.48.28:8000/docs)
- Тип модели `question-answering`, модель `timpal0l/mdeberta-v3-base-squad2`.
- Модель возвращает ответ на вопрос пользователя на основании переданного контекста. Вопрос отправляется методом POST на адрес `http://158.160.48.28:8000/predict/`. Тело запроса: json объект с двумя переменными, в переменной `text` собственно отправляется вопрос к модели. 
_____
**Пример тела запроса (json):**
```json
{
  "text": "Как называется ваша компания?",
  "num": 0
}
```
______
**Пример curl запроса:**
```bash
curl -X 'POST' \
  'http://158.160.48.28:8000/predict/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "text": "Как называется ваша компания?",
  "num": 0
}'
```
______
**Пример 200 ответа (body response):**
```json
{
  "score": 0.9657419323921204,
  "start": 21,
  "end": 29,
  "answer": " IVITECH"
}
```

*Виртуальную машину создавал на примере из лекции и выбрал опцию "прерываемая". Поэтому нет гарантий, что на момент просомтра ДЗ ВМ будет работать.*


_____
## Шешин Н.А. 
### Задание 1
Выбран тип модели Zero-Shot Image Classification. Модель - openai/clip-vit-large-patch14. В скрипте sheshin_clip.py представлен пример запуска данной модели.

### Задание 2
Было разработано web-приложение на основе библиотеки streamlit. Данное приложение организует работу с ранее выбранной моделью для классификации изображений на произвольных классах.

Код состоит из:
1. Обертка для модели - [Practice2/clip_classifier.py](https://github.com/nasheshin01/URFU_ML_PI/blob/master/SheshinProject/Practice2/clip_classifier.py)
2. Скрипт конструирующий само web-приложение - [Practice2/page.py](https://github.com/nasheshin01/URFU_ML_PI/blob/master/SheshinProject/Practice2/page.py)

Приложение:
- Запускается приложение с помощью команды - ```streamlit run page.py```
- Скриншоты работы приложения можно найти в папке [Practice2/screenshots](https://github.com/nasheshin01/URFU_ML_PI/blob/master/SheshinProject/Practice2/screenshots)

