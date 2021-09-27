# Red Hat OpenShift - Desplegar MySQL ☁

## Índice  📰
1. [Pre-Requisitos](#Pre-Requisitos-pencil)
2. [Desplegar base de datos MySQL](#Desplegar-base-de-datos-MySQL-floppy_disk)

### Opción 1 💡
4. [Acceso a la base de datos y CRUD con IBM Cloud Shell](#Acceso-a-la-base-de-datos-y-CRUD-con-IBM-Cloud-Shell-hammer-computer)

### Opción 2 💡
5. [CRUD con MySQL Workbench](#CRUD-con-MySQL-Workbench-wrench-gear)
6. [Referencias](#Referencias-mag)
7. [Autores](#Autores-black_nib)
<br />

## Pre Requisitos :pencil:
* Contar con una cuenta en <a href="https://cloud.ibm.com/"> IBM Cloud</a>.
* Contar con un clúster en OpenShift.
* Opcional: instalación de <a href="https://www.mysql.com/products/workbench/"> MySQL Workbench</a> (en caso de realizar CRUD con esta herramienta - Opción 2). 
<br />

<p align="center"><img width="700" src="https://github.com/emeloibmco/IBM-Cloud-PostgreSQL-Despliegue/blob/main/Im%C3%A1genes/EliminarDatos.gif"></p>

<br />


## Desplegar base de datos MySQL :floppy_disk:
Para realizar el despliegue de una base de datos MySQL en un clúster de OpenShift, complete los siguientes pasos:
<br />

1. Dentro de su cuenta de *IBM Cloud* acceda al ```IBM Cloud Shell``` dando click en la pestaña <a href="https://cloud.ibm.com/shell"> <img width="25" src="https://github.com/emeloibmco/IBM-Cloud-PostgreSQL-Despliegue/blob/main/Im%C3%A1genes/Shell_IBM.PNG"></a>, que se ubica en la parte superior derecha del portal. 
<br />

2. Ingrese a la consola web de OpenShift. Posteriormente de click sobre su correo (parte superior derecha) y luego en la opción ```Copy Login Command```. Una vez cargue la nueva ventana, de click en la opción ```Display Tokeny```. Copie el comando que sale en la opción ```Log in with this token``` y colóquelo en el IBM Cloud Shell para iniciar sesión y acceder a su clúster de OpenShift.
<br />

3. En la consola de OpenShift cree un nuevo proyecto. Para ello, asegúrese de estar en el rol de ```Developer```, de click en la pestaña ```Project``` y luego ```Create Project```. Allí, asígne un nombre y de click en el botón ```Create```.
<br />

4. Acceda al proyecto creado en IBM Cloud Shell. Para ello utilice el comando:

   ```
   oc project <nombre_proyecto>
   ```

   Ejemplo:

   ```
   oc project mysql-project
   ```
   <br />

5. Realice una búsqueda en el catálogo sobre los recursos relacionados con MySQL que pueden ser desplegados en el clúster. Para ello coloque el comando:

   ```
   oc new-app --search mysql
   ```
   <br />

6. Despliegue el template de MySQL. Para este caso hay dos opciones que puede utilizar:
   * Sin almacenamiento persistente (```mysql```).
   * Con almacenamiento persistente (```mysql-persistent```).
   <br />
   
   Para este caso, se utiliza la plantilla con almacenamiento de volumen persistente, ya que esto permite que los datos sobrevivan y no se pierdan cuando el pod se reinicie. Por otro lado, en el despliegue se deben indicar algunas variables de entorno para la configuración del servidor. Utilice el comando:
   
   ```
   oc new-app mysql-persistent --param=MYSQL_USER=user --param=MYSQL_PASSWORD=pass --param=MYSQL_DATABASE=prueba --name mysql
   ```
   
   > NOTA: Las varibles definidas permiten configurar el usuario, contraseña y nombre de la base de datos MySQL. Estos datos se necesitarán más adelante cuando acceda a la base de datos.
   <br />

7. Verifique el estado de implementación de la base de datos. Para ello coloque el comando:

   ```
   oc status
   ```
   <br />

8. Obtenga los pods de la MySQL y verifique que el despliegue se ha completado con éxito. Utilice el comando:

   ```
   oc get pods
   ```
   <br />

## Opción 1 💡
## Acceso a la base de datos y CRUD con IBM Cloud Shell :hammer: :computer:
<br />

## Opción 2
## CRUD con MySQL Workbench :wrench: :gear:
<br />


## Referencias :mag:
* <a href="https://cloud.ibm.com/docs/databases-for-postgresql?topic=databases-for-postgresql-getting-started"> Get Started PostgreSQL</a>.
<br />


## Autores :black_nib:
Equipo IBM Cloud Tech Sales Colombia.
<br />
