# Cutter-Model
Модель для определения склеек кадров в фильмах

## Запуск предобученных моделей
Дать ссылки для быстрого запуска модели локально или в colab. А так же ссылки на модель и датасет с HaggingFace.

## Введение
Приветствую всех в моём разборе решения задачи нахождения склеек в фильмах! Во-первых, стоит объяснить зачем мне пришлось находить склейки. В марте 2023 года проходил хакатон по созданию AI решений по двум трекам, одним из которых звучал так: "Аудиосопровождение происходящего на экране для людей с нарушением зрения". Наше решение вы можете посмотреть <a href='https://github.com/Aleshka5/MTS_UAI_Team'>тут</a>.<br>

Как понятно из названия задача заключалась в изучении фильмов средствами AI. Одним из первых решений нашей команды было описать каждую сцену отдельно (далее подход мы улучшили, но сейчас не об этом). Так, информация не перемешивалась при смене локации и действующих лиц, ведь они порой не связаны друг с другом напрямую. После чего я занялся решением этой задачи.
![МТС борд](https://github.com/Aleshka5/Cutter-Model/assets/78702396/b61396d6-1124-4cc5-8cd9-4b8aff03b53a)

## Постановка задачи
Для начала разберёмся в природе склеек и их типах. <br>

> <b>Склейка</b> (в данном разборе) - два кадра, которые принадлежат разным локациям, сценам, ракурсам одной сцены и т.д.

То есть, если камеру выключили и переместили, а потом продолжили снимать, то мы будем искать этот момент по двум соседним кадрам. Такой подход оптимален в 95% случаев.<br>
![Склейка пример 1 rus](https://github.com/Aleshka5/Cutter-Model/assets/78702396/ecc96631-dd14-49d5-b290-65b82f0359a5)
### Классификация склеек
Тут всё просто, есть три типа склеек: 
<ol>
  <li>Явная склейка</li>
  <li>Плавное наложение разных сцен</li>
  <li>Плавное затемнение (засветление)</li>
</ol>
Последние два типа склеек как правило и будут составлять 5% ошибок, потому что в них кадры меняются плавно (не считая динамичных моментов, когда нейросеть просто ошибается внутри одной сцены).

![Пример тип 2 и тип 3 rus](https://github.com/Aleshka5/Cutter-Model/assets/78702396/1656b30f-8636-47ab-a641-136ecee50a6e)

## Предобработка данных и сбор датасета
Для начала решения задачи я решил написать не большой скрипт для удобного сбора и разметки датасета. Сам датасет я решил собирать из 4 трейлеров к фильмам, которые в сумме длятся не более 20ти минут. Трейлеры очень плотно нафаршированы склейками и потому они мне и понравились.

Для начала работы с видео мы должны перевести их в список кадров и привести к одному размеру, у меня это будет 544x1280, так как при таком соотношении сторон обычно снимают фильмы и это достаточное разрешение, чтобы нейросеть работала быстро и замечала детали на видео. Так как фильмы больше трейлеров, а весь фильм покадрово в RAM не поместится приходим к выводу, что стоит заранее позаботится о его постепенной обработке. Фильм мы будем обрабатывать кусками (батчами).
```python
def myfoo():
  print('!')
```
### Сбор данных
Как я писал скрпт для сбора данных и как потом размечал их в полуавтоматическом режиме

### Стандартизация размера входных данных
Решение проблемы различных форматов 

### Аугментация датасета 
Как из маленького датасета сделать огромный

### Проблема чёрных экранов
описание проблемы и её решение
## Различные подходы и их точность
### Метрики

### Архитектура с двумя изображениями

### Архитектура с разностью изображений

### Заключение и сравнение с уже существующими аналогами

## Выводы
