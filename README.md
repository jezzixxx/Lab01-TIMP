# Lab01-ТиМП
## Плышевская К. ИУ8-23. Лабораторная работа по ТиМП №1

### 1) Скачайте библиотеку boost с помощью утилиты wget
#### `wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz`
Скачать библиотеку boost

### 2) Разархивируйте скаченный файл в директорию
#### `tar -xf archive.tar.gz`
+ tar —работа с архивом
+ -x — режим распаковки
+ -f — наименование файла

### 3) Подсчитайте количество файлов в директории не включая вложенные директории.
#### `find . -maxdepth 1 -type f| wc`
+ find — команда для поиска файлов и каталогов на основе специальных условий;
+ -maxdepth - максимальная глубина поиска по подкаталогам, для поиска только в текущем каталоге установите 1.
+ -type f — искать только файлы.
+ wc — счётчик (1-е число — строк, 2-е — слов, 3-е — байт)
__Ответ: 12__

### 4) Подсчитайте количество файлов в директории включая вложенные директории.
#### `find . -type f| wc `
Убирая ограничение максимальной вложенности, найдём все файлы во всех папках)
##### Ответ: 61191
### 5) Подсчитайте количество файлов с расширением .cpp
#### `find . -name "*.cpp" | wc` 
-name — поиск по наименованию. "*" заменяет неизвестные данные
##### Файлов cpp: 13774
### Заголовочных файлов, 
#### `find . -name "*.h" -o -name "*.hpp" | wc`
-o — (or) или
##### Заголовочных файлов (hpp или h): 15208
### Сколько остальных файлов (не заголовочных и не .cpp)
#### `find . -not \( -name "*.h" -o -name "*.hpp" -o -name "*.cpp" \) -type f | wc`
(необходимо добавить -type f, чтобы не учитывать папки
скобки конкатенации)
##### Остальные: 32209

### 6) Найдите полный пусть до файла any.hpp внутри библиотеки boost.
#### `find . -name "any.hpp"`
##### Ответ:
###### ./boost/fusion/include/any.hpp
###### ./boost/fusion/algorithm/query/any.hpp
###### ./boost/fusion/algorithm/query/detail/any.hpp
###### ./boost/type_erasure/any.hpp
###### ./boost/any.hpp
###### ./boost/proto/detail/any.hpp
###### ./boost/xpressive/detail/utility/any.hpp
###### ./boost/spirit/home/support/algorithm/any.hpp
###### ./boost/hana/any.hpp
###### ./boost/hana/fwd/any.hpp

### 7) Выведите в консоль все файлы, где упоминается последовательность boost::asio.
#### `grep -lr boost::asio`
+ grep — поиск строки в файлах
+ -l — вывод только имени файла
+ -r — рекурсивный поиск

### 8) Скомпилирутйе boost.
#### `./bootstrap.sh --prefix=boost_output --with-python=python3 --with-icu=`
создать конфигурацию сборки с поддержкой юникода и питона
### 
#### `./b2 install`
скомпилировать файлы

### 9) Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
#### `mkdir ~/boost-libs `
Создание папки boost-libs
### 
#### `cd ~/boost_1_69_0/boost_output/lib`
Переход в папку boost_output/lib
### 
#### `mv * ~/boost-libs`
перенос всех файлов из ~/boost_1_69_0/boost_output/lib в  ~/boost-libs

### 10) Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
#### `cd ~/boost-libs/`
Переходим в папку ~/boost-libs/ , где находятся библиотеки теперь
### 
#### `du -s` 
размер выводится в кБ по умолчанию

### 11) Найдите топ10 самых "тяжёлых".
#### `du -s * | sort -nr | head`
+ sort — сортировка
+ -n — (numeric) по числовым значениям
+ -r — в рекурсивном порядке
+ head — выводит первые строки (умолчание — 10)
