# Trabajo Individual 

Nombre: Alan Giovanni Mora Vargas
Celular : 62615493

## Clase 1

### Que es Git?
Sistema de control de versiones distribuido (VCS). Checkpoint de un videojuego.
Nos permite guardar archivos y las versiones de estos a lo largo del tiempo de manera
local, permitiendo volver a cambios anteriores en caso de cometer algun error.

### Como nacion Git?
Creador de Linux -> Linus Torvalds
Antes de Git las contribuciones eran enviadas por correo hacia Linus, al recibir demasiadas solicitudes y que termine revisando codigo anterior con el codigo actual, donde aplicar el cambio de multiples personas hacia que el proceso sea demasiado cansador, por lo que inicio con el uso de herramientas como BitKeeper (privados), vio que existian demasiados reglas de privacidad, las rompio y le quitaron el acceso, viendo este problema decide hacerlo el mismo entre 2 a 3 semanas creando GIT.

### Como instalar Git?
Debemos dirigirnos a la pagina web de GIT y seguir los pasos de instalacion recomendados para el S.O. en uso y luego verificar la correcta instalacion escribiendo en la terminal:
```
git --version
```

### Configuraciones basicas
git config --global user.name "Nombre_Usuario"
git config --global user.email "correo@.com"
git config --global core.autocrlf true
git config --list

### Archivos que todo repo deberia tener
    Readme.md -> archivo con el objetivo de redactar 
    .gitignore -> archivos a ignorar en el repositorio.

Uso para titulos
#    
Subtitulos
##
Parrafo normal
...
Codigo
```
Aca viene el codigo
```

## No hice los apuntes de estos dias debido a que no me encuentraba muy bien de salud
## Respaldado por Saul Cordova Villarroel.

## Clase 2

### Los estados de Git

#### Directorio de trabajo (Modificado)
    La carpeta local donde la diferencia es que GIT observa sus cambios y los cataloga:
        Untracked -> Sin seguimiento, se lo ve pero no tiene una version antigua de ese archivo, sucede cuando este es creado.
        Modified -> Es cuando GIT ya tiene una version previa del archivo y lo modificaste4, eliminaste o cambiaste el nombre.

    Cualquier archivo que no este en el .gitignore pasa automaticamente a uno de esto estados dependiendo que se haya hecho. Considerar que aca escribimos codigo pero GIT aun no lo tiene "asegurado".

    Queremos que un archivo vuelva a su estado original, que pase de modified a su estado original 
    ```
    git restore <archivo>
    ```
    Borrando fisicamente lo que se escribio, tener cuidado.

    No quiero que el archivo que cree lo vea GIT?
    Agregamos el nombre del archivo completo al .gitignore
#### Stage Area (Preparado)
    El area de espera. Le decimos a GIT: "Esto es lo que quiero guardar".

    Esta area nos permite seleccionar quue archivos modificados se incluiran en el siguiente commit (guardado) y cuales no.

    Para traer un archivo de stage area lo que debes hacer es:
    ```
    git add <archivo> : Agrega el archivo <archivo>, lo hace uno por uno.
    git add . : Agrega todos los archivos que sean observados por GIT.
    ```

    Si queremos sacar un archivo del stage area para volver a un estado anterior:
    ```
    git restore --staged <archivo>
    ```
#### Repositorio Local (Confirmado)
    El historial; Los cambios ya tiene un ID (hash) y son parte de la historia.
    Esta es la ultima fase, aqui es donde le decimos al repositorio que cree el punto de guardado para que todos los cambios que estan en staged pasen a ser parte del historial.
    ```
    git commit -m "mensaje"
    ```

    Para deshacer el ultimo commit el comando es:
    ```
    git reset --soft HEAD~1
    ```

<img src="images/imagenUno.png" alt="Imagen sobre estados clase dos" />

#### .gitignore
    Realiza el no seguimiento a distintos archivos marcados en este archivo.
#### Buenas practicas en commits
Cada cuanto debo hacer un commit?
El uso de commits es de tipo atomicos, donde cada cambio representa un unico cambio logico, pequenio y completo en el codigo fuente. Es mejor hacer commits pequenios, agrupando las mejoras o acciones, la idea no es hacer commits sin sentidos, sino que sean leves progresos en interacciones pequenias que tengan un significado permitiendo a la aplicacion o proyecto funcionando.

Escribe buenos commits.
    a. Un commit debe describir lo que hace en pocas palabras y de manera simple pero efectiva.
    b. Verbos Imperativos:
        Add : Significa que se agrega un nuevo archivo
        Change : Significa que se modifica un archivo existente
        Fix : Significa que se arregla un bug
        Remove : Elimina un archivo existente
    c. No usar punto final y puntos suspensivos
        git commit -m “Add new search feature.”  X
        git commit -m “Fix a problem with topbar..”  X
        git commit -m “Change the default system color” BIEN
    d. Usar como maximo 50 caracteres
        Ser corto y preciso, si hay mucho que explicar es que el commit contenga demasiados cambios.
    e. Usar un prefijo para los commits haciendolos mas semanticos
        Para que el historial sea legible y se sepa mas facilmente lo que se hace se usa este tipo de
        commits:
        Escribe buenos commits
            git commit -m “<tipo de commit>: <descripción>”
        Por ejemplo:
            git commit -m “feat: Add new search feature”
    f. Añade todo el contexto que se necesario en el cuerpo del commit
        Proveer todo el contexto necesario a un commit, en lugar de saturar el sumario del commit, aniadir informacion que sea necesaria en el cuerpo del mensaje. Para ello utilizamos git commit, donde la primera linea sea el titulo y la segunda linea sea el cuerpo, aplicar reglas de puntuacion.
## No hice los apuntes de estos dias debido a que no me encuentraba muy bien de salud
## Respaldado por Saul Cordova Villarroel.

## Clase 3
### Que es GitHub?
Github es una plataforma en la nube y red social para desarrolladores que permite alojar, gestionar y colaborar en proyectos de software utilizando Git.

### Git Vs GitHub
Git es un sistema de control de versiones que crea los puntos de guardado y GitHub es el servidor donde esos puntos se almacenan y se socializan con el mundo. GitHub usa Git pero no son lo mismo.

### Generar conexion con GitHub
La conexion se realizar a partir de modo que sea requerido, ya sea por ssh o por https, ya sea para repositorios nuevos (por crear) como para repositorios ya creados se siguen una cantidad de pasos que nos permite conectar nuestro Git con GitHub, algunos comandos son:
```
git remote add origin git@github.com ...
git push origin branch -> empujar cambios a una rama
git remote -v -> visualizar a que repositorio remotes esta conectando
git clone ... -> Clonacion de un repositorio
ssh-ketgen -t ed255519 -C "correo@gmail.com" -> generar llave privada para la conexion con github por medio de configuracion ssh
git commit --amend -m 'mensaje' -> este comando agarra el ultimo commit y modifica el mensaje por el nuevo descrito 
```

### Manipulacion de cambios 
Existen dos comandos para manipular los cambios ya sean realizados anteriormente y falta existe una falta de actualizacion:
```
git pull origin [nombre_rama]
```
este comando actualiza los cambios de una rama especifica
el siguiente comando permite empujar todos los cambios realizados en tu maquina local, enviando al servidor el codigo actualizado trabajado en este tiempo
```
git push origin [nombre_rama]
```
## No hice los apuntes de estos dias debido a que no me encuentraba muy bien de salud
## Respaldado por Saul Cordova Villarroel.

## Clase 4
### Que es git remote?
Comando que nos permite gestionar nuestra conexiones 

### Multiples SSH
Es como tener tuneles con distintas puertas, donde cada puerta tiene su propio cerrojo que es abierto por una sola llave especifica.
```
ssh-keygen -t ed25519 -C "correo@gmail.com" -f ~/.shh...[colocar la direccion donde queremos almacenar la key generada.]
```
Considerar que la direccion debe ser para un archivo unico porque sino sobreescribira sobre uno ya existente.

<img src="images/imagenDos.png" alt="Imagen para conexion ssh en github" />

Cada ssh generada con el objetivo de utilizarlo en github debe ser agregada en la seccion de la imagen.

Para utilizar otra ssh solo debemos hacer la modificacion por medio del comando
```
git remote set-url origin git@github-auxi:[url_repositorio] -> ahora con un usuario distinto
git remote set-url origin git@github.com:[url_repositorio] -> antes con el usuario principal
```
Para cambiar la configuracion local de la global simplemente no debemos tener en cuenta el --global

### Que es git checkout?
Es el comando que nos permite desplazarnos, visualizando esos puntos de guardados.
Nos sirve para inspeccionar (ver como era el codigo de un commit antiguo).
Restaurar (Recuperar archivos borrados o cambiados).
Experimentar (Probar cambios sin arruinar la rama principal).
Cambiar (Saltos de una rama a otra / ej. de main a desarrollo).
Es posible hacer cambios experimentales a commits anteriores ya almacenados y no en los actuales, el commit no desaparece
por lo menos por los siguientes 30 dias, para conservar tenemos que almacenarlos en un rama aparte para posteriormente unirlos
No es lo recomendado hacer esto, preferible mantener una buena practica y solo para hacer una revision al codigo anterior.
Si hay algo en area de staging, no se puede aplicar el checkout, no podremos ver cambios anteriores y demas.
