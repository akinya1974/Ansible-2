# 7.1. Ansible - Павел Голиков
## Задание 1
Какие преимущества дает подход IAC?
Приведите ответ в свободной форме.
* скорость
* воспроизводимость
* масштабируемость
* не нужна ручная настройка
## Задание 2
1.Установите Ansible.
2.Настройте управляемые машины (виртуальные или физические, не менее двух).
3.Создайте файл инвентори. Предлагается использовать файл, размещенный в папке с проектом, а не файл инвентори по умолчанию.
4.Проверьте доступность хостов с помощью модуля ping.
Приложите скриншоты действий.
1.Установите Ansible. 
vagrant up 3-х хостов  из этого [Vagrantfile](/Vagrantfile)
на host0 ставил ansible, host1 и host2 - управляемые.
![t2-1](/scrshts/t2-1.png)
2.Настройте управляемые машины (виртуальные или физические, не менее двух).
На каждом хосте sudo nano /etc/ssh/sshd_config :
![t2-2](/scrshts/t2-2.png)
и sudo service ssh restart .
На host0: ssh-copy-id vagrant@192.168.33.11; ssh-copy-id vagrant@192.168.33.12
3.Создайте файл инвентори. Предлагается использовать файл, размещенный в папке с проектом, а не файл инвентори по умолчанию
На host0: sudo cp /etc/ansible/ansible.cfg ~/test/ansible.cfg; sudo nano ~/test/ansible.cfg :
![t2-3](/scrshts/t2-3.png)
и nano ~/test/hosts : 
![t2-4](/scrshts/t2-4.png)
4.Проверьте доступность хостов с помощью модуля ping.
![t2-5](/scrshts/t2-5.png)
На host1 и host2: sudo apt update; sudo apt install python-pip 
С host0: 
![t2-6](/scrshts/t2-6.png)
## Задание 3
Какая разница между параметрами forks и serial?
Приведите ответ в свободной форме.
forks - максимальное количество одновременных подключений, выполняемых Ansible для каждой задачи.
serial - определяет количество узлов, обрабатываемых в каждой задаче за один запуск.
## Задание 4
В этом задании мы будем работать с Ad-hoc коммандами.
1.Установите на управляемых хостах пакет, которого нет(любой).
2.Проверьте статус любого присутствующего на управляемой машине сервиса.
3.Создайте файл с содержимым "I like Linux" по пути /tmp/netology.txt
Приложите скриншоты запуска команд.
1. ![t4-1](/scrshts/t4-1.png)
2. ![t4-2](/scrshts/t4-2.png)
3. ![t4-3](/scrshts/t4-3.png)
## Задание 5
Напишите 3 playbook'a. При написании рекомендуется использовать текстовый редактор с подсветкой синтаксиса YAML. Плейбуки должны:
1.Скачать какой либо архив, создать папку для распаковки и распаковать скаченный архив. Например, можете использовать официальный сайт и зеркало Apache Kafka https://kafka.apache.org/downloads. При этом можно качать как исходный код, так и бинарные файлы (запакованные в архив), в нашем задании не принципиально.
2.Установить пакет tuned из стандартного репозитория вашей ОС. Запустить его как демон (конфигурационный файл systemd появится автоматически при установке). Добавить tuned в автозагрузку.
3.Изменить приветствие системы (motd) при входе на любое другое по вашему желанию. Пожалуйста, в этом задании используйте переменную для задания приветствия. Переменную можно задавать любым удобным вам способом.
Приложите файлы с плейбуками и вывод выполнения.
1. ![t5-1](/scrshts/t5-1.png)
2. ![t5-2](/scrshts/t5-2.png)
3. ![t5-3](/scrshts/t5-3.png)
## Задание 6
Задание модифицировать playbook из 3 пункта 5 задания:
Playbook должен в качестве приветствия установить ip адрес и hostname усправляемого хоста, пожелание хорошего дня системному администратору.
Приложите файл с модифицированным плейбуком и вывод выполнения.
![t6](/scrshts/t6.png)
## Задание 7
Создайте playbook, который будет включать в себя одну, вами созданную роль. Роль должна:
1.Установить веб сервер Apache на управляемые хосты.
2.Сконфигурировать файл index.html c выводом характеристик для каждого компьютера. Необходимо включить CPU, RAM, величину первого HDD, ip адрес.
3.Открыть порт 80 (если необходимо), запустить сервер и добавить его в автозагрузку.
4.Сделать проверку доступности веб сайта(ответ 200).
Приложите архив с ролью и вывод выполнения.
![t7](/scrshts/t7.png)
