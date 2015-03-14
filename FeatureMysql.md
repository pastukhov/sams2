#### Создание пользователя MySQL ####

Для работы SAMS необходимо в MySQL создать пользователя со всеми правами на базы squidctrl и squidlog.
MySQL позволяет создать пользователя и назначить ему базу до того, как сама база будет создана.

#### Создание пользователя вручную ####

Зайдите в консоль MySQL:

mysql -u root -p (Если у вас пароль пользователя root пустой, ключ -p не используйте)

Выполните там команды:

GRANT ALL ON squidctrl.**TO sams@localhost IDENTIFIED BY "yourpassword";**

GRANT ALL ON squidlog.**TO sams@localhost IDENTIFIED BY "yourpassword";**

Где:

yourpassword - пароль

Занесите имя пользователя и пароль в файл конфигурации SAMS /etc/sams.conf


#### 2. Создание базы данных SAMS ####

Из каталога mysql выполните скрипты **create\_sams\_db** и **create\_squid\_db**.

Эти скрипты по-умолчанию выполняются от имени пользователя, прописанного в sams.conf.

Если у вас в sams.conf прописан пользователь root, а пароль пользователя mysql root оставлен по-умолчанию (пустой), отредактируйте скрипты, удалив из строк

mysql -u $USER -p < xxxx\_db.sql ключ -p