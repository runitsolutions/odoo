# Odoo

[![Logo](img/logo.png)](https://github.com/runitcr/odoo)

Colección Ansible para instalar Odoo.

## Índice

- [Instalación](#instalación).
- [Playbooks](#playbooks).
- [Roles](#roles).
- [Dependencias](#dependencias).
- [Desarrollo](#desarrollo).
- [Licencia](#licencia).
- [Autor](#autor).

## Instalación

Para instalar la colección ejecute los siguientes pasos.

Instale la colección:

```
ansible-galaxy collection install git@github.com:runitcr/odoo.git
```

Esto instalará la colección en la ruta
`~/.ansible/ansible_collections/runitcr/odoo`.

Instale los roles dependencia:

```
ansible-galaxy install -r ~/.ansible/collections/ansible_collections/runit/odoo/requirements.yml
```

## Playbooks

Se listan los playbooks incluidos en esta colección.

| Nombre | Descripción | Ejecución |
| --- | --- | --- |
| [odoo](playbooks/odoo.yml) | Instala y configura Odoo. | `ansible-playbook runit.odoo.odoo -i inventory.yml -l mi_grupo` |

## Roles

Se listan los roles incluidos en esta colección.

| Nombre | Descripción |
| --- | --- |
| [odoo](roles/odoo/README.md) | Instala y configura Odoo. |

## Dependencias

### Colecciones

- [community.general](https://docs.ansible.com/ansible/latest/collections/community/general/index.html).

### Roles

- [coopdevs.odoo-role](https://github.com/coopdevs/odoo-role).

### Python

- [ansible](https://pypi.org/project/ansible).
- [flake8](https://pypi.org/project/flake8).
- [molecule-lxd](https://pypi.org/project/molecule-lxd).
- [voluptuous](https://pypi.org/project/voluptuous).
- [yamllint](https://pypi.org/project/yamllint).

## Compatibilidad

- Ansible >= 2.10.
- Debian Bullseye.
- Ubuntu Jammy.
- Python 3.

## Desarrollo

Si desea modificar la colección por ejemplo para agregar variables o
para modificar un rol, **debe clonar** el repositorio de la colección:

```
git clone git@git.runitcr.org:runit/odoo.git ansible_collections/runit/odoo
```

El repositorio se clonará en la ruta `ansible_collections/runit/odoo`,
esta ruta es requerida por Ansible para poder ejecutar el comando
[ansible-test](https://www.ansible.com/blog/introduction-to-ansible-test)
usado para probar la colección.

Para configurar el ambiente de desarrollo, siga los pasos:


### ansible-test

Para ejecutar la herramienta oficial
[ansible-test](https://www.ansible.com/blog/introduction-to-ansible-test), siga
lose pasos descritos a continuación.

Instale [docker y docker-compose](https://docs.docker.com/engine/install/debian).

Acceda al directorio de la colección:

```
cd ansible_collections/runit/odoo
```

Para ejecutar las pruebas de sanidad corra el comando:

```
ansible-test sanity
```

Para ejecutar las pruebas de integración corra el comando:

```
ansible-test integration --docker ubuntu2004
```

### Python

- Instale  [Pip](https://pypi.org/project/pip):

```
sudo apt install -y python3-pip
```

- (Opcional) Instale
  [Pipenv](https://pipenv-es.readthedocs.io) y cree un ambiente virtual:

```
python3 -m pip install pipenv
python3 -m pipenv shell
```

- Instale los requerimientos de Python:

```
pipenv install
```

### Molecule

- Acceda al rol que se quiere probar:

```
cd roles/test_role
```

- Ejecute las pruebas de [Molecule](https://molecule.readthedocs.io):

```
molecule test
molecule converge
```

- Verifique la dirección IP del contenedor con el comando:

```
lxc ls

+---------------------+---------+----------------------+----------------------------------------------+-----------+-----------+
|        NAME         |  STATE  |         IPV4         |                     IPV6                     |   TYPE    | SNAPSHOTS |
+---------------------+---------+----------------------+----------------------------------------------+-----------+-----------+
| instance-standalone | RUNNING | 10.242.156.69 (eth0) | fd42:e76e:88c:c577:216:3eff:fe5c:e564 (eth0) | CONTAINER | 0         |
+---------------------+---------+----------------------+----------------------------------------------+-----------+-----------+
```

- Use la dirección IP para acceder al contenedor.

- También puede ingresar al contenedor ejecutando:

```
molecule login
```

## Licencia

GPL 3.

## Autor

![Runit](img/autor.png)

[Runit](https://runitcr.com).