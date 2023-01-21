# Ansible
Напишите плейбук, который будет на удаленной системе создавать пользователя user1 и задавать ему SSH-ключ (создавая заданный ключ в /home/user1/.ssh/id_rsa.pub). 
Ключ не должен передаваться в открытом виде. Используйте для шифрования ключа ansible-vault. Ключ можете сгенерировать, используя SSH-keygen.

Создать пользователя
useradd -m user1

Задать пароль
passwd user1

Добавить юзера в sudoers
echo -e 'user1\tALL=(ALL)\tNOPASSWD:\tALL' > /etc/sudoers.d/user1

Зашифровать пароль
mkpasswd --method=sha-512

Скопировать хеш в файл 
/etc/ansible/playbooks/secret.yml

залогиниться под user1/сгенерировать ssh-keygen
ssh-keygen -t rsa

Шифруем ключ
ansible-vault encrypt id_rsa.pub
Создаем файл для vault-id -secrets.txt сохраняем в нем пароль для дешифровки

Запускаем
ansible-playbook add_user.yml --vault-id id_rsa.pub@secrets.txt -kK
