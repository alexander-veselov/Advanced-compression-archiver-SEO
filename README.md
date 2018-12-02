# Advanced: compression, archiver, SEO

## Структура проекта
* **Data** - папка с необходимыми для работы файлами
* **Source** - "независимые" исходики; запускаются с параметрами; например, **py arithmetic.py c input.txt output.txt**
* **Utilities** - там находится чекер

## Параметры запуска программ
* **archiver.py** mode directory file
  - mode - "a": архивировать, "e": разархивировать
  - directory - путь для сжатия
  - file - файл для создания архива
* **arithmetic.py** mode input output
  - mode - "c": сжать, "d": распаковать
  - input - файл, который необходимо сжать / распаковать
  - output - файл, в который необходимо сжать / распаковать
* **seoanalysis.py** input
  - input - файл, который необходимо анализировать
  
## Структура папки Data
* **Archive** - папка, в которой находится архив, создаваемый с помощью **archiver.py**
* **Compressed** - папка, содержащая файлы, сжатые программой **arithmetic.py**
* **Decompressed** - папка, содержащая файлы, распакованные программой **arithmetic.py**
* **Directory** - папка, содержащая файлы, а также другие папки разного уровня вложенности
* **Extracted** - папка, в которую разархивируется архив
* **Input** - папка, содержащая текстовые файлы, используемые **arithmetic.py** и **seoanalysis.py**

## clean.py
* Очищает все результаты работы программ
* Оставляет лишь входные файлы
* Если после запуска данного скрипта у вас форматнулась половина диска, я не виноват :)

## Файл конфигурации
* В программе используется файл конфигурации **config.ini**
* Используется лишь в работе runnner'ов
* В нем прописаны пути папок, перечисленных ранее
* Для использования данного файла конфигурации был написан модуль **config.py**

## Чекер
* **cheker.py** input output
* Сравнивает директории input и output и файлы в них
* Используется в runner'ах для тестирования корректности работы
  
## Описание runnner'ов
* **ArchiverRunner.py**
  - С помощью **archiver.py** собирает архив папки **Directory**
  - Созданный архив находится в папке **Archive**
  - Использует сжатие - **arithmetic.py**
  - Распаковывает собранный ранее архив в папку **Extracted**
  - Запускает чекер для папок **Directory** и **Extracted**
* **CompressRunner.py**
  - Запускает **arithmetic.py** для каждого файла в папке **Input**
  - Сжатые файлы находятся в папке **Compressed**
  - Распакованные файлы находятся в папке **Decompressed**
  - Запускает чекер для папок **Compressed** и **Decompressed**
* **SEORunner.py**
  - Запускает **seoanalysis.py** для каждого файла в папке **Input**
  - Выводит на экран полученную информацию
  
## Результаты работы
* 
