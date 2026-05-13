# Лабораторная работа №3

Lotnik Vladislav IU8-23

## Задание 1

Вам поручили перейти на систему автоматизированной сборки CMake. Исходные файлы находятся в директории [formatter_lib](formatter_lib). В этой директории находятся файлы для статической библиотеки `formatter`.

[CMakeLists.txt](formatter_lib/CMakeLists.txt)

## Задание 2

У компании "Formatter Inc." есть перспективная библиотека, которая является расширением предыдущей библиотеки.

[CMakeLists.txt](formatter_ex_lib/CMakeLists.txt)

## Задание 3

Для демонстрации работы с библиотекой `formatter_ex` были созданы два приложения:

- `hello_world`, которое использует библиотеку `formatter_ex`.
- `solver`, которое использует статические библиотеки `formatter_ex` и `solver_lib`.

[CMakeLists.txt](hello_world_application/CMakeLists.txt)

[CMakeLists.txt](solver_application/CMakeLists.txt)
