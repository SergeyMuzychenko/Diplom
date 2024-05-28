# Diplom
Ключевая задача — разработать отказоустойчивую инфраструктуру для сайта, включающую мониторинг, сбор логов и резервное копирование основных данных. Инфраструктура должна размещаться в Yandex Cloud и отвечать минимальным стандартам безопасности.



### 1\. Для выполнения задания был написан манифест terraform [main.tf](https://github.com/SergeyMuzychenko/Diplom/blob/main/terraform/main.tf), котрый созает следующие ресурсы:

#### 1.1 Виртуальные машины.

  - bastion-host
  - elast
  - kibana
  - web-server-nginx-2
  - web-server-nginx-1
  - zabbix

<details>
<summary> Скриншот(-ы) </summary>

![01_vm](https://github.com/SergeyMuzychenko/Diplom/blob/main/1.png)

</details>


</details>

#### 1.2 Группы безопасности соответствующих сервисов на входящий трафик только к нужным портам


<details>
<summary> Скриншот(-ы) </summary>

![09_20SG](https://github.com/SergeyMuzychenko/Diplom/blob/main/2.png)

</details>

#### 1.3 Балансировщик нагрузки для распределения запросов на сайт и обеспечения безопасности

<details>
<summary> Скриншот(-ы) </summary>

![02_target-group](https://github.com/SergeyMuzychenko/Diplom/blob/main/3.png)

![03_backend-group](https://github.com/SergeyMuzychenko/Diplom/blob/main/4.png)

![7](https://github.com/SergeyMuzychenko/Diplom/blob/main/5.png)

![7](https://github.com/SergeyMuzychenko/Diplom/blob/main/6.png)

![7](https://github.com/SergeyMuzychenko/Diplom/blob/main/7.png)

![7](https://github.com/SergeyMuzychenko/Diplom/blob/main/8.png)

![7](https://github.com/SergeyMuzychenko/Diplom/blob/main/9.png)

</details>

### 2. Установка и настройка серверов на ВМ производилась с помощью плэйбуков  Ansible.


[файл host inventory](https://github.com/lantsevrot/Diplom/blob/main/ansible/hosts)**

[elasticsearch_playbook.yaml](https://github.com/lantsevrot/Diplom/blob/main/ansible/elastik_playbook.yaml)**

[kibana_playbook.yaml](https://github.com/lantsevrot/Diplom/blob/main/ansible/kibana_playbook.yaml)**
   
[nginx-playbook.yaml](https://github.com/RaffaelX/sys-gitlab-hw/blob/main/_diplom/ansible/nginx-playbook.yaml), [main.yml](https://github.com/RaffaelX/sys-gitlab-hw/blob/main/_diplom/ansible/nginx/tasks/main.yml)

[filebeat_playbook.yaml](https://github.com/lantsevrot/Diplom/blob/main/ansible/filebeat_playbook.yaml)

[zabbix_agent_playbook.yaml](https://github.com/lantsevrot/Diplom/blob/main/ansible/zabbix_agent_playbook.yaml), [main.yml](https://github.com/lantsevrot/Diplom/blob/main/ansible/roles/zabbix-agent/tasks/main.yml)

[zabbix_server_playbook.yaml](https://github.com/lantsevrot/Diplom/blob/main/ansible/zabbix_server_playbook.yaml), [main.yml](https://github.com/lantsevrot/Diplom/blob/main/ansible/roles/zabbix-server/tasks/main.yml)


### 3. Резервное копирование 
#### 3.1 Резервное копирование было настроено через terraform, подробрнее в файле main.tf

<details>
<summary> Скриншот(-ы) </summary>

![99_Snapshot_1](https://github.com/SergeyMuzychenko/Diplom/blob/main/10.png)


</details>
