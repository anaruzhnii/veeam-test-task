# Тестовое задание Veeam

## Запуск

### Из Visual Studio
Если программа увидит подключенный дебаггер или не найдет аргументов запуска, она попросит ввести путь до файла и размер блока

### Из командной строки
Аргументы:
  Что | Зачем 
--- | --- 
**--input-path** path  | Путь до входного файла
**--output-path** path  | *Необязателен.* Путь до файла с результатом расчета. Если не указан, вывод будет производиться в консоль
**--block-size** block-size | Размер блока
**--single-thread** | *Необязателен.* Если указан, программа будет выполняться в однопоточном режиме
**--hash-algorithm-name** hash-algorithm-name | *Необязателен.* Название алгоритма хэширования, по умолчанию - SHA256