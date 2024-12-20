# Детектирование объектов на изображении с помощью модели Yolox-Tiny.

Структура лабораторной работы:
1. Для обработки модели используется программный интерфейс `YoloxTiny`, в котором реализованы следующие методы:
    * `__init__` - конструктор класса, который принимает путь до модели и вспомогательный класс-обертку `Image`, после чего сохраняет их в свои внутренние поля;
    * `_get_net_from_path` - метод класса, который считывает модель средствами `OpenCV`, проверяя корректность передаваемого пути до модели;
    * `set_input` - метод, предназначенный для инициализации входа нейросетевой модели перед инференсом;
    * `inference` - метод, предназначенный для запуска инференса нейросетевой модели;
    * `nms` - метод, реализующий алгоритм `non-naximum supression`;
    * `multiclass_nms_class_agnostic` - метод, отсеивающий выходы по заданному порогу уверенности;
    * `demo_postprocess` - метод для обработки выходов модели `Yolox-Tiny`, который строит сетку с заданными шагами для вычисления координат прямоугольников;
    * `output_process` - метод, внутри которого происходит парсинг выхода модели и использование методов `demo_postprocess` и `multiclass_nms_class_agnostic`;
2. Для обработки видео используется программный интерфейс `Video`, в котором реализованы следующие методы:
    * `__init__` - конструктор класса, который принимает путь до видео и файл с классами;
    * `frame_detect` - метод, который покадрово обрабатывает видео и рисует на них прямоугульники;
    * `gen_video` - метод, который из обработанных кадров собирает видео;
3. Для обработки изображения используется программный интерфейс `Image`, в котором реализованы следующие методы:
    * `__init__` - конструктор класса, который принимает путь до изображения;
    * `_get_image` - метод, который возвращает представление изображения в виде тензора;
    * `preprocess_image` - метод, который вычитает среднее по выборке и делит на стандартное отклонение входное изображение;