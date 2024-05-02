# Laboratory work I
Данная лабораторная работа посвещена изучению утилит для разработки проектов
# Tasks
- [x] 1. Ознакомиться со ссылками учебного материала
- [x] 2. Выполнить инструкцию учебного материала
- [x] 3. Составить отчет и отправить ссылку личным сообщением в Slack
# Homework
1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания
```
https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.
```

`wget https://sourceforge.net/projects/boost/files/boost/1.69.0/b^Cst_1_69_0.tar.gz`

Ответ: [Task1](https://gist.github.com/PhilippD3/1548888ac452a49855c1caedf7eb520a)

2. Разархивируйте скаченный файл в директорию `~/boost_1_69_0`:

```
 tar -xf boost_1_69_0.tar.gz

 rm -rf boost_1_69_0.tar.gz (Удаляем архив)
```
3. Подсчитайте количество файлов в директории `~/boost_1_69_0` не включая вложенные директории:
``` 
/boost_1_69_0$ find . -maxdepth 1 -type f | wc -l 
```

Ответ: 12

4. Подсчитайте количество файлов в директории `~/boost_1_69_0` включая вложенные директории. 
```
/boost_1_69_0$ 
find -type f|wc -l
```

Ответ: 61191

5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp):
```
/boost_1_69_0$ find . -type f -name "*.cpp"|wc -l
```

Ответ: 13774

```
/boost_1_69_0$ find . -type f -name "*.hpp"|wc -l
```

Ответ: 14912

```
/boost_1_69_0$ find . -type f -name "*.h"|wc -l
```

Ответ: 296

```
/boost_1_69_0$ find . -type f -not -name ".h" -and  -type f -not -name ".hpp" -and  -type f -not -name ".cpp" | wc -l 
```

Ответ: 61191

6. Найдите полный пусть до файла `any.hpp` внутри библиотеки boost:
```
 find $(pwd) -name any.cpp
```

Ответ:
```
/home/vboxuser/boost_1_69_0/libs/hana/example/any.cpp
/home/vboxuser/boost_1_69_0/libs/fusion/test/algorithm/any.cpp
```

7. Выведите в консоль все файлы, где упоминается последовательность `boost::asio` :
```
$ find . -type f -exec grep -l "boost::asio" {} + > task7
```

Ответ: [Task7](https://gist.github.com/PhilippD3/208198623fc837314f18944ec7727a85)

8. Скомпилирутйе boost:
```
cd boost_1_69_0/tools/build
sh bootstrap.sh
./b2 install --prefix=out
```

Ответ: [Task8](https://gist.github.com/PhilippD3/c552a60f37dbf46085a747d60f132671)

9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boost-libs`:
```
mv out boost-libs
```

10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории:

Ответ: [Task10](https://gist.github.com/PhilippD3/76e18b67e6e66e493f8aba9a128bba9f)

11. Найдите топ10 самых "тяжёлых":

`/boost_1_69_0/tools/build/boost-libs$ find . -type f -exec du {} +|sort -rh | head -n 10 `

Ответ:
```
288	./bin/bjam
288	./bin/b2
80	./share/boost-build/src/tools/msvc.jam
64	./share/boost-build/src/build/targets.jam
60	./share/boost-build/src/tools/msvc.py
60	./share/boost-build/src/build/targets.py
56	./share/boost-build/src/build/project.py
52	./share/boost-build/src/tools/gcc.jam
48	./share/boost-build/src/build/project.jam
48	./share/boost-build/src/build/generators.py
```
```
Copyright (c) 2015-2021 The ISC Authors
```