# Приложение для обнаружения нефтяных разливов #
## Этапы анализа 
1. Выделение черного цвета на снимке 
>Это выполняется путем наложения на кадр цветового фильтра в заданном диапазоне
2. Разбиение отфильтрованной картинки на квадраты 
>Размер квадратов можно изменять. По умолчанию он составляет 0.063 от ширины изображения
3. Поиск нефти в квадрате 
>Это происходит при помощи сравнения количества черных пикселей и заданного числа (общее количество пикселей в квадрате, умноженное на определенный коэффициент, по умолчанию 0.003)
4. Определение результата
>Номера квадратов с нефтью добавляются в список. Если он оказывается непустым, то на снимке есть нефть.

## Развертывыние приложения на сервере

### Установка сервера

>Для начала следует установить веб-сервер для удобного отображения директорий с 
>фотографиями после их обработки, например, [Apache](https://httpd.apache.org/).

### Установка Python и библиотек

>Установите Python 3 на сервер. После этого установите необходимые для работы
>приложения библиотеки и фреймворки с помощью менеджера пакетов pip, 
>используя следующие команды:
>```bash
>pip install Flask
>pip install opencv-python
>pip install --upgrade Pillow
>pip install numpy
>```

### Установка путей для сохранения изображений

>Когда пользователь обращается к приложению, то оно загружает
>все изображения, полученные от пользователя, в специальную директорию.
>После завершения работы приложения, изображения распределяются 
>по другим директориям в зависимости от наличия нефтяных
>разливов на фотографии.<br><br>
>Вам необходимо указать путь к директории, в которую изначально будут
>загружаться все изображения от пользователя на вашем сервере
>в файле **main.py**. Укажите в качестве значения константы **UPLOAD_FOLDER**
>путь к этой директории.<br><br>
>Позже в этом же файле в качестве значения константы **REDIRECT_URL**
>укажите путь к директории, которая будет содержать директории с изображениями
>после завершения работы алгоритма.<br><br>
>В файле **detector.py** в качестве значения константы **PATH_SUCCESS**
>установите путь к директории, в которую после работы алгоритма
> должны быть помещены изображения, на которых **будут обнаружены** нефтяные
>разливы. А в качестве значения константы **PATH_FAIL** установите путь
>к директории, в которой будут изображения, на которых **не будут обнаружены**
>нефтяные разливы. 

### Запуск приложения

>Загрузите файлы **main.py** и **detector.py** на сервер.<br><br>
>Запустите приложение. Например, с помощью данной команды:
>```bash
>nohup python3 main.py &
>```
