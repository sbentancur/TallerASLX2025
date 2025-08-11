# TallerASLX2025

Para un correcto uso de este repositorio, se parte de la base de que las siguientes VM están instaladas en el ambiente y tienen conexión entre sí:
-	Ubuntu 24.04 
-	CentOS Stream 9
  
Se definen las siguientes “IPs” y “hostnames” correspondientes:
> - ubuntu01: 192.168.1.10
> - centos01: 192.168.1.15
> - bastion01: 192.168.1.20

Existe el usuario “sysadmin” en todos los equipos y se conoce la clave “root” para una eventual elevación de permisos durante la ejecución. 
Clave SSH fue generada y compartida en Bastion hacia los demás “hosts” mediante “ssh-copy-id” 

# Pasos para ejecutar el repositorio:
1.	Copiar SSH de Github: Hacer click en CODE y copiar la opción de HTTPS
2.	En Bastion01, instalar como administrador ansible-core 
    > _$ sudo dnf install ansible-core -y && dnf install git -y_
3.	Estando en directorio home, se copia el repositorio localmente
    > _$ cd ~ && git clone (pegar git)_
4.	Se comprueba que haya conexión activa entre los hosts
    > _$ ansible -i 192.168.1.15,192.168.1.10, all -m ping_
    > _$ ansible all -m ping_
5.	Se instalan módulos necesarios
    > _$ ansible-galaxy install -r collections/requirements.yaml_
6.	Se ejecutan comandos “ad-hoc”
7.	Se ejecutan “playbooks” generales
    > _$ ansible-playbook all playbook/hardening.yaml -K_
