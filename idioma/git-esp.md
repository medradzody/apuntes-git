<!-- <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet">  -->

<body style="text-align: justify; font-family: 'Ubuntu';">

<h1 style="font-weight: 800; text-align: left">📍Indice</h1>

- [¿Qué es un Sistema de Control de Versiones?](#qué-es-un-sistema-de-control-de-versiones)
- [Sistema de Control de Versiones Locales:](#sistema-de-control-de-versiones-locales)
- [Sistema de Control de Versiones Centralizados:](#sistema-de-control-de-versiones-centralizados)
- [Sistema de Control de Versiones Distribuidos:](#sistema-de-control-de-versiones-distribuidos)
- [Operaciones locales en Git:](#operaciones-locales-en-git)
- [Los tres estados de Git:](#los-tres-estados-de-git)
- [Las tres áreas de un proyecto de Git:](#las-tres-áreas-de-un-proyecto-de-git)
- [Flujo de trabajo en Git:](#flujo-de-trabajo-en-git)
- [Configuración de Git inicial:](#configuración-de-git-inicial)
- [Configurar tus credenciales:](#configurar-tus-credenciales)
- [Ayuda rápida:](#ayuda-rápida)

<h1 style="font-weight: 800;">GIT y Github</h1>
Para iniciar debemos de aclarar que cuando hablamos de Git, hacemos alusión a un sistema de control de versiones (VCS). Cabe resaltar que sin duda es el más utilizado en el mundo. Además es un proyecto de código abierto que hace énfasis en optimizar su rendimiento. Por otro lado durante el desarrollo del kernel de Linux (1991 - 2002), los cambios que se realizaban en el software eran a través de parches y archivos. No fue hasta el 2002 cuando su kernel empezó a usar un DVCS llamado BitKeeper. Por diferentes problemas en 2005 la relación que había entre la comunidad desarrolladora del kernel de Linux y BitKeeper, esta herramienta dejó de ser gratuita. Esto "obligó" a Linus Torvalds a desarrollar su propia hermamienta basada en BitKeeper. Desde 2005 Git ha evolucionado y es tremendamente rápido, así como fácil de usar y tiene un buen sistema de ramificación (Branching). 

---

#### ¿Qué es un Sistema de Control de Versiones?
También conocido como "control del código fuente". Es un sistema que registra y gestiona cambios realizados en un archivo o conjunto a lo largo del tiempo. Esto nos permite recuperar versiones específicas en cualquier momento. Por ejemplo si eres programador y tu código dejó de compilar satisfactoriamente, puedes regresar a versiones pasadas para poder analizar y comparar tu código hasta encontrar el error. De mismo modo si se te llega a corromper algún archivo, tendrás siempre una copia para poder respaldarlo.

---

#### Sistema de Control de Versiones Locales:
En la actualidad muchas personas crean sus Sistemas de Control de Versiones Locales sin saberlo, y quizás tu también lo has hecho. En algún momento tenías una carpeta que querías respaldar, y lo que hiciste fue copiarla y llevarla a otro directorio, incluso mientras ibas avanzando le ponías de nombre la hora, la fecha, etc. Lo malo es que este método es propenso a fallar, ya que realmente no estás siguiendo un patrón que te pueda asegurar no sobreescribir tus archivos, e incluso pudo pasar que para poder ver los cambios en un archivo tuviste que entrar carpeta por carpeta y perder aún más tiempo. No obstante aquí nace la solución. El Sistema de Control de Versiones Locales, que funciona através de una pequeña base de datos donde se registran todos los cambios realizados en un archivo de manera local.

<img src="https://images4.programmerclick.com/887/2b/2ba5091dd058e1b07a18a62d5bd81a4f.png" alt="Gráfico de sistema de control de versiones local"/>

---

#### Sistema de Control de Versiones Centralizados:
Imaginate que buscas colaborar con algún compañero de equipo, y trabajar en el mismo archivo en simultáneo, la solución para poder hacerlo fue crear un CVS (Sistema de Control de Versiones Centralizados) que utiliza un servidor padre/central donde se almacenan todos los archivos. Este trabaja sobre un repositorio único. No obstante una desventaja importante sería que si el servidor central/padre se cae, pues las conexiones enlazadas a este también lo harían y no se podría guardar cambios en él. Por otro lado si el disco duro se corrompo y no hay copias de seguridad existentes, se perderá toda la información. En pocas palabras, cuando tienes tu proyecto completo en un mismo lugar, te arriesgas a perderlo todo.

<img src="https://www.opentix.es/wp-content/uploads/2019/02/articulo_img1.png" alt="Gráfico de sistema de control de versiones centralizado"/>

---

#### Sistema de Control de Versiones Distribuidos:
Ahora llegamos a los Sistemas de Control de Versiones Distribuidos (DVCS) que llegan a solucionar los problemas de los Sistemas de Control de Versiones antes mencionados. La principal diferencia es que no dependen de un servidor central, ya que cada cliente genera una copia local o "clon" del repositorio principal; es decir, cada cliente mantiene un repositorio local propio que contiene todos los archivos y metadata del repositorio principal. Es así que los clientes pueden actualizar sus repositorios locales con nuevos datos del servidor central, con una operación llamada "pull" y enviar los nuevos cambios con "push" desde su repositorio local.

<img src="https://www.opentix.es/wp-content/uploads/2019/02/articulo_img2.png" alt="Gráfico de sistema de control de versiones distribuidos"/>

---

#### Operaciones locales en Git:
A diferencia de otros CVCS donde se trabaja por medio de la red, ya que en cada instante se hace una petición al servidor, en git se hace una copia de la historia del proyecto localmente haciendo que la petición sea casi inmediata ya que se trabaja con el disco duro local. Además si necesitas un archivo antiguo Git localmente se pondrá a buscarlo ahorrándose el trabajo de ir a un servidor y hacer la petición. Por esto se dice que se puede trabajar normalmente con Git de manera offline (Sin conexión a internet) y poder guardar los cambios en tu base de datos local hasta volver a estar en línea y subirlo todo.

---

#### Los tres estados de Git:
Es muy importante entender que en Git se manejan 3 estados principales a la hora de trabajar con algún cambio en tu archivo.
  -  **Confirmado - Committed:** Significa que los datos ya están almacenados de manera segura en tu base de datos local. (Guardado en repositorio local).
  -  **Modificado - Modified:** Significa que has modificado el archivo pero aún no lo has confirmado en tu base de datos local.
  -  **Preparado - Staged:** El fichero ha sido marcado para que vaya en tu próximo commit. (Es un área de cambios pendientes antes del commit).

---

#### Las tres áreas de un proyecto de Git:
  -  **Directorio de Git - Git directory:** Aquí se almacenan los metadatos y la base de datos de objetos para tu proyecto. Además es la parte más importante de Git, es lo que se copia cuando clonas un repositorio desde otra computadora. 
  -  **Directorio de Trabajo - Working directory:** Significa que has modificado el archivo pero aún no lo has confirmado en tu base de datos local.
  -  **Área de preparación - Staging area:** Significa que has seleccionado al archivo para que vaya en t

<img src="https://miro.medium.com/max/686/1*diRLm1S5hkVoh5qeArND0Q@2x.png" alt="Gráfico de sistema de control de versiones distribuidos"/>

---

#### Flujo de trabajo en Git:
  - **Modificas los archivos** en tu directorio de trabajo.
  - **Preparas los archivos**, añadiéndolos al área de preparación.
  - **Confirmas los cambios** (Los archivos que se encuentren en el área de preparación). Se generará una nueva copia instantánea en tu directorio de Git. Recordar que cuando hablamos de copias instantáneas nos referimos a copias que trabajan en versiones. Es decir si existe un cambio pues sólamente se grabará lo que haya variado, más no toda la copia, ya que lo haría pesado. Esto es bueno, ya que si tenemos un archivo de 10GB y modificamos algo, pues no tendremos que hacer otra copia de 10GB, si no sólo lo que se modifico.

---

#### Configuración de Git inicial:
Para poder empezar a trabajar de git debemos de modificar unas cuantas cosas a través de nuestra terminal. Todo esto lo podemos configurar en cualquier momento. Para poder acceder a esta herramiento lo hacemos mediante el comando ***git config***. Este en resumidas cuentas nos permite modificar/obtener variables de configuración que modifican el funcionamiento de Git, estas pueden ser tu nombre de usuario, tu correo electŕonico, etc...

---

#### Configurar tus credenciales:
Una vez instalado procedemos a estableces tu nombre de usuario y contraseña de correo electrónico. Además cabe resaltar que esta información debe ser real y si haces uso de alguna plataforma de Github debe coincidir. Esto es por que cuando tu envias un commit (Estás confirmando tus archivos para ser enviados) se incluirá esta información. 

```bash
$ git config --global user.name "tu_nombre_de_usuario_entre_comillas"
$ git config --global user.email tu_correo@ejemplo.com
```
Con la opción ```--global``` se indica que esta configuración se usará en todo el sistema, por lo que si quieres sobreescribirla, usa ```--global``` de la misma forma. Así mismo para comprobar tu información usa el siguiente comando.

```bash
$ git config --list
user.email=tu_correo@ejemplo.com
user.name=tu_nombre_de_usuario_entre_comillas
```

Por otro lado si tu quieres encontrar una clave específica.

```bash
$ git config <clave>
$ git config user.email
tu_correo@ejemplo.com
```

---

#### Ayuda rápida:
Te recomiendo ir jugando con los comandos de git, no obstante puedes encontrarlos si escribes el siguiente comando. Donde clave es la sección de cofiguración que necesitas, por ejemplo "config" como lo vimos anteriormente.

```bash
$ git help <clave>
$ git <clave> --help
```

---

## Obteniendo repositorio en Git:
Este capítulo es muy importante y empezaremos a adentrarnos más a Git. Se mostrará el conocimiento básico con el que serás capaz de trabajar con Git. Además cabe resaltar que en git tienes dos maneras de obtener un proyecto, la primera es por medio de un directorio existente es importarlo. La segunda es clonar un repositorio existente desde otro servidor.

#### Inicializando un repositorio en un directorio existente:
Nos dirigimos al directorio del proyecto donde buscamos trabajar y escribimos:

```bash
$ git init
```

Te darás cuenta que se creará una nueva carpeta .git, si no la ves activa las carpetas ocultas. Esta carpeta contiene todos los archivos necesarios. Debemos recordar que este comando sólo necesitamos ejecutarlo una vez, y será durante la configuración inicial.

#### Clonando un repositorio existente:
Muchas veces buscaremos "clonar" un repositorio existente, para eso usaremos el comando:

```bash
$ git clone [URL_A_CLONAR]
```

No obstante debemos entender que cuando clonamos desde un repositorio existente, se descargarán todas las versiones de este mismo. Por otro ya que los archivos se descargan de manera local, si nosotros guardamos cambios y lo enviamos a nuestro repositorio local no afectará al remoto, no obstante podemos sincronizarlos.

```bash
$ git clone https://github.com/medradzody/apuntes_git
```

La interpretación de arriba sería, crear un nuevo directorio llamado apuntes_git, donde cuenta con un .git en su interior que usa para descargar toda la información de ese repositorio y posteriormente crea una copia de la última versión. Si entras en la carpeta encontrarás todos los archivos y subdirectorios del repositorio remoto. No obstante si quieres cambiar el nombre del directorio que se creará, puedes usar este comando.

```bash
$ git clone https://github.com/medradzody/apuntes_git otroNombre
```

---

#### Estado de tus archivos:
Para saber el estado de nuestros archivos hacemos uso del comando:

```bash
$ git status
On branch main
nothing to commit, working directory clean
```

Si te apareció el mensaje de arriba significa que no hay archivos modificados ni rastreados. Y te dice que te encuentras en la rama por defecto (Se le conoce como main/master). Más adelante veremos como trabajar con diferentes ramificaciones. Por otro lado si creas un archivo por ejemplo README.md (Este archivo se usa para dar una introducción acerca de tu proyecto y está escrito en markdown). Te aparecerá lo siguiente.

```bash
$ touch README.md
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
  README
nothing added to commit but untracked files present (use "git add" to track)
```

Debajo de "Untracked files" podemos notar que nos dice que el archivo README no está siendo rastreado (rastrear es que Git nota nuevos archivos que no habían en el commit anterior). Cabe resaltar que git sólo lo incluirá si se lo indicas explícitamente, de la siguiente manera.

```javascript
$ git add <Nombre del archivo>
// Para añadir un archivo específico.
$ git add README
// Para añadir todo.
$ git add .
```
Cuando ponemos "." al final de todo estamos indicando que queremos añadir TODO, Ahora si tu tratas de ver en que estado está nuestro proyecto, tendremos:

```javascript
$ git status
$ Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   README.md
```

Aquí lo que nos dice en resumidas cuentas es que el archivo ya está siendo rastreado.

---

#### Git status abreviado
:
Podemos hacer uso de un comando abreviado para simplificar la operación con git status. Se usarán ejemplos para poder entender esto.

```bash
$ git status -s 
  D  .gitignore
  D  0_git.md
  AM README.md
  A  idioma/git-eng.md
  AM idioma/git-esp.md
```

| Indicador | Significado                              |
| --------- | ---------------------------------------- |
| ??        | Archivos nuevos que no están rastreados. |
| A         | Archivos preparados.                     |
| M         | Archivos modificados.                    |

---

#### Ignorar archivos en Git:
Si en algún momento quisiésemos decirle a Git que no rastree un tipo de archivo, lo haríamos mediante un archivo llamado .gitignore. Este lo debemos de crear en nuestro directorio tal cual y dentro del mismo pondremos las condiciones, por ejemplo no quiero rastrear los archivos que terminen en .ejemplo, para ello lo agregaría en el archivo .gitignore, tal que así:

```
RECORDAR QUE ESTAMOS DENTRO DE .gitignore (DEBEMOS CREARLO)

# Ignoramos archivos terminados en .ejemplo
*.ejemplo

# No ignorar específicamente "esteno.ejemplo", los demás .ejemplo serán ignorados
!esteNo.ejemplo

# Ignorar TODOS los archivos dentro de un directorio
directorioCualquiera/

# Ignorar sólo el directorio padre con nombre directorioPadre
/directorioPadre

# Ignora TODOS los archivos .txt del directorioEjemplo/
directorioEjemplo/**/*.txt
```

Si quieres una lista más completa, puedes ingresar [AQUÍ](https://github.com/github/gitignore) para conocer templates de.gitignore creados para diferentes proyectos.

</body>