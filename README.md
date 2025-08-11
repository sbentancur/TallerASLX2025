# Trabajo Obligatorio TallerASLX2025

> [!NOTE]
> Para un correcto uso de este repositorio, se supone que las siguientes VM están instaladas en el ambiente y tienen conexión entre sí:
-	Ubuntu 24.04 
-	CentOS Stream 9


Se definen las siguientes “IPs” y “hostnames” correspondientes:
> - ubuntu01: 192.168.1.10
> - centos01: 192.168.1.15
> - bastion01: 192.168.1.20

> [!IMPORTANT]
> - Existe el usuario “sysadmin” en todos los equipos y se conoce la clave “root” para una eventual elevación de permisos durante la ejecución. 
> - Clave SSH fue generada y compartida en Bastion hacia los demás “hosts” mediante “ssh-copy-id” 


# Pasos para ejecutar el repositorio:
1.	Copiar SSH de Github: Hacer click en CODE y copiar la opción de HTTPS
2.	En Bastion01, instalar como administrador "ansible-core"
  - [ ] `$ sudo dnf install ansible-core -y && dnf install git -y`
3.	Estando en directorio "home", se copia el repositorio localmente
  - [ ]  ` $ cd ~ && git clone (pegar git)`
4.	Se comprueba que haya conexión activa entre los "hosts"
  - [ ] `$ ansible -i 192.168.1.15,192.168.1.10, all -m ping`
  - [ ] `$ ansible all -m ping`
5.	Se instalan módulos necesarios
  - [ ] `$ ansible-galaxy install -r collections/requirements.yaml`
6.	Se ejecutan comandos “ad-hoc”
7.	Se ejecutan “playbooks” generales
  - [ ] `$ ansible-playbook all playbook/hardening.yaml -K`
  - [ ] `$ ansible-playbook all playbook/nfs_setup.yml) -K`
