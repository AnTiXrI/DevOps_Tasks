# DevOps_Tasks
### A few DevOps tasks with solutions 

## Содержание
- [Task 1](#task-1)
- [Task 2](#task-2)
- [Комманды для Linux](#комманды-для-linux)
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









## Комманды для Linux
### ps aux
ps - process status «состояние процесса»  
- a: Отображает процессы всех пользователей, а не только текущего пользователя.  
- u: Форматирует выходные данные с учетом пользовательских данных, таких как использование процессора и памяти.  
- x: Включает процессы без подключённого терминала, такие как демоны и фоновые службы.

 Первичные состояния:  
**R**: Запущен или готов к выполнению.  
**S**: Спит, ожидая события или сигнала.  
**I**: незанятый поток ядра  
**D**: Непрерывистый сон (обычно связан с операциями ввода-вывода).  
**Z**: Zombie — завершенный процесс, ожидающий удаления своим родителем.

Ключевые атрибуты:  
**s**: Руководитель сеанса  
**N**: Низкий приоритет  
**<**: Высокий приоритет  
 
Например, STAT значение Ss обозначает лидера спящего сеанса, в то время как l< указывает бездействующий поток ядра с высоким приоритетом.  

### awk
Простейшая форма команды awk подразумевает описание основного действия в одинарных кавычках и фигурных скобках с указанием после него целевого файла: **awk '{action}' your_file_name.txt**  
Виды:  
- **awk '/regex pattern/{action}' your_file_name.txt** - Когда вам нужно найти текст, соответствующий конкретному шаблону, или же конкретное слово в тексте  
- **awk '{print $0}' information.txt** - Вывод всего файл ( как cat )  
- **awk '{print $1}' information.txt** - Вывод первого  
- **awk '{print $1, $4}' information.txt** - Для вывода 1 и 4  
- **awk '{print $NF}' information.txt** - Вывод последнего  
- **awk '{print $1}' information.txt | head -1** - Вывод опредленного столбца  
- **awk '/^O/' information.txt** - Вывод строк с начинающ. с опред буквы  

