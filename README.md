# Application for detecting oil slicks on images #
The analysis process is divided into several stages:
1. Highlight black color in the picture
>This happens by applying a color filter to the frame in a given range (min_p, max_p)
2. Splitting the filtered image into squares 
>The size of the squares can be changed. By default it is 0.063 of the image width
3. Searching for oil in squares 
>Comparing the number of black pixels and a given number (total number of pixels in a square multiplied by a certain factor, default 0.03)
4. Determining the result and coloring the marked squares if necessary
>After searching for oil squares, we get a list of numbers. If it is not empty, then there is oil.

# Развертывыние приложения на сервере

## Установка сервера

>Для начала следует установить веб-сервер для удобного отображения директорий с 
>фотографиями после их обработки, например, [Apache](https://httpd.apache.org/).

## Установка Python и библиотек

>Установите Python 3 на сервер. После этого установите необходимые для работы
>приложения библиотеки и фреймворки с помощью менеджера пакетов pip, 
>используя следующие команды:
>```bash
>pip install Flask
>pip install opencv-python
>pip install --upgrade Pillow
>pip install numpy
>```

## Установка путей для сохранения изображений

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

## Запуск приложения

>Загрузите файлы **main.py** и **detector.py** на сервер.<br><br>
>Запустите приложение. Например, с помощью данной команды:
>```bash
>nohup python3 main.py &
>```
