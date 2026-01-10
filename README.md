# DevOps_Tasks
### A few DevOps tasks with solutions 
## Task 1
Description: A developer created a testing program that is continuously writing to a log file /var/log/bad.log and filling up disk. You can check for example with tail -f /var/log/bad.log.
This program is no longer needed. Find it and terminate it. Do not delete the log file. 
  
Описание: Разработчик создал тестовую программу, которая непрерывно пишет в лог файл /var/log/bad.log и забивает диск. Можно проверить с помщью tail -f /var/log/bad.log. Эта программа больше не нужна. Необходимо найти ее и отключить. Не удаляя лог файл  
### Solution/Решение 
Смотрим запущенные процессы с помощью __ps aux__  
Находим процесс и его PID  
Убиваем его с помощью kill PID
