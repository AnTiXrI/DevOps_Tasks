# DevOps_Tasks
### A few DevOps tasks with solutions 

## Содержание
- [Task 1](#task-1)
- [Task 2](#task-2)
## Task 1
Description: A developer created a testing program that is continuously writing to a log file /var/log/bad.log and filling up disk. You can check for example with tail -f /var/log/bad.log.
This program is no longer needed. Find it and terminate it. Do not delete the log file. 
  
Описание: Разработчик создал тестовую программу, которая непрерывно пишет в лог файл /var/log/bad.log и забивает диск. Можно проверить с помщью tail -f /var/log/bad.log. Эта программа больше не нужна. Необходимо найти ее и отключить. Не удаляя лог файл  
### Solution/Решение 
Смотрим запущенные процессы с помощью __ps aux__  
Находим процесс и его PID  
Убиваем его с помощью kill PID

## Task 2
Description: There's a web server access log file at /home/admin/access.log. The file consists of one line per HTTP request, with the requester's IP address at the beginning of each line.  
Find what's the IP address that has the most requests in this file (there's no tie; the IP is unique). Write the solution into a file /home/admin/highestip.txt.  

Описание: В файле /home/admin/access.log находится журнал доступа веб-сервера. Каждая строка файла соответствует одному HTTP-запросу, и в начале каждой строки указан IP-адрес отправителя запроса.  
Найдите IP-адрес, с которого поступило наибольшее количество запросов в этом файле (совпадений нет; IP-адрес уникален). Запишите решение в файл /home/admin/highestip.txt.
### Solution/Решение
Смотрим первые строчки : **awk '{print $1}' /home/admin/access.log**  
Для записи в файл используем : ** awk '{print $1}' /home/admin/access.log | sort | uniq -c > /home/admin/highestip.txt  

~ uniq — это утилита для фильтрации или подсчёта подряд идущих одинаковых строк в текстовом потоке.  
~ Ключевой момент: uniq работает только с отсортированными данными, потому что сравнивает только соседние строки. Если одинаковые строки не находятся рядом, они не будут обработаны как дубликаты!  
~ uniq -c : счетчик 
