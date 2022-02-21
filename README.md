# GitTraining
Git es un proyecto de código abierto maduro y con un mantenimiento activo que desarrolló originalmente Linus Torvalds, el famoso creador del kernel del sistema operativo Linux, en 2005. Un asombroso número de proyectos de software dependen de Git para el control de versiones, incluidos proyectos comerciales y de código abierto.

Por ejemplo, supongamos que una desarrolladora, Alice, hace cambios en el código fuente (añade una función para la próxima versión 2.0) y, luego, los confirma con mensajes descriptivos. Después, trabaja en una segunda función y confirma también esos cambios. De forma natural, estos se almacenan como elementos independientes de trabajo en el historial de versiones. A continuación, Alice cambia a la rama de la versión 1.3 del mismo software para corregir un error que afecta únicamente a esa versión anterior. El objetivo es permitir al equipo de Alice lanzar una publicación de corrección de errores, la versión 1.3.1, antes de que la 2.0 esté lista. Tras ello, Alice puede volver a la rama 2.0 para seguir trabajando en las nuevas funciones de la versión. Todo esto puede tener lugar sin necesidad de acceso a la red y, por consiguiente, es un proceso rápido y fiable. Alice podría incluso hacerlo mientras viaja en avión. Cuando esté lista para enviar al repositorio remoto todos los cambios confirmados de modo individual, bastará con que utilice un solo comando.

## Tutorial 0: Instalar Git

Antes de comenzar con este entrenamiento, debemos asegurarnos de tener git en nuestro sistema operativo. Cabe mencionar que la mayoría de las distribuciones de **Linux** cuentan por defecto con Git.

Las instrucciones de instalación para **Windows** son las siguientes:

1. Descargar el [instalador de Git para Windows](https://git-for-windows.github.io/) más reciente.
2. Iniciar el instalador y completarlo seleccionando las opciones *Next* y *Finish*. Para facilitar la utilización, se recomienda activar la casilla **Utilizar Git desde el símbolo del sistema de Windows**.
3. Abrir el símbolo del sistema utilizando las teclas *Windows + X* de tu teclado, luego seleccionar *Windows PowerShell*.
4. Configurar Git utilizando el siguiente comando, reemplazando los datos con la información asociada a tu cuenta Github:

        git config --global user.name "John Smith" git config --global user.email "eparis@atlassian.com"

## Tutorial 1: Clonar un repositorio
Github es un repositorio online gratuito que permite gestionar proyectos y controlar versiones de código. 

Un repositorio es la ubicación o ruta en la que se almacena toda la información de un proyecto como imágenes, código, carpetas, documentos, etc. Cada proyecto contaría con su propio repositorio único, por lo que la ruta de acceso será exclusiva para el proyecto.

Hace algún tiempo, Github realizó mejoras de seguridad y con ello ahora es necesario una contraseña "adicional" cada vez que se desee realizar una acción sobre un repositorio. La forma más sencilla es creando un *Personal access token*, el cual asociará una cuenta Github con uno o más computadores.

Para crearlo, se debe visitar la página [Developer settings](https://github.com/settings/tokens) de Github clickeando sobre la imágen de perfil, seguido de *Settings* y *Developer settings*. Una vez allí, presionar el botón *Generate new token* y rellenar el formulario, seleccionando todas las casillas de **repo**. Se recomienda anotar el sistema operativo del computador junto con el utilizador (por ejemplo "Windows 10 - Computador Acer") y una fecha de expiración, ya que éste método es potencialmente peligroso. Una vez creado el token, copiar el código que comienza con "ghp_" y guardarlo para el paso número 4.

1. Visitar el repositorio que se quiere clonar. En nuestro caso, el repositorio actual.
2. Presionar el botón verde *Code* y copiar la dirección web que comienza con "https".
3. Abrir el símbolo del sistema y navegar hasta la carpeta *Documents*. En Windows, por defecto se comienza en "C:\Users\nombreUsuario" por lo que basta acceder escribiendo el comando:
        
        cd .\Documents\
  
4. Una vez dentro, escribir el comando:
  
        git clone direcciónURLdelRepositorio
  
5. Ingresar el nombre de usuario y el token generado previamente.

Y listo! El repositorio ha sido descargado en tu computador, creando una **versión local**. Este proceso es llamado clonación.

## Tutorial 2: Cambiar de rama
Como en el ejemplo mencionado anteriormente, los proyectos tienden a implementar nuevas funciones (o *features*) a medida que van creciendo.

Las ramas de Git proveen una forma segura de implementar estos cambios, ya que cada rama se encuentra aislada de las otras y por tanto no comprometen al repositorio principal. Para que esto tenga sentido, Git tiene un puntero llamado **HEAD**, el cuál apuntará a una rama en específico.

Cada vez que se crea una nueva rama, esta se basa en una ya existente, permitiendo hacer las modificaciones deseadas al contenido seleccionado.

Con Github es fácil ver la cantidad de ramas existentes en un repositorio. En la parte de arriba, a la izquierda, podrás notar un botón con un ícono y un título que dice **main** (que es la rama actual). Al presionarlo, se desplegarán todas las ramas activas de este repositorio. Vamos a cambiarnos a la rama **dev**.

1. En el símbolo del sistema, ubicados dentro de la carpeta del proyecto, escribir:

        git checkout -b dev

Este comando crea una nueva rama **local** llamada dev y a la vez mueve nuestro HEAD a ella. Se recomienda utilizar el nombre de la rama remota (osea, la que se encuentra en el repositorio) para la rama local.

2. Luego utilizar el comando:

        git pull origin dev

Este comando descarga los archivos que se encuentran en la rama **remota** dev **en este momento**. Este proceso es a veces llamado "pulear".

Y ya está! ahora nuestra versión local se encuentra en una nueva rama y está actualizada.

## Tutorial 3: Hacer cambios
Si estás viendo este mensaje, es por que aún no cuentas con los archivos de la rama remota dev. Repite el tutorial anterior y vuelve a abrir este archivo README.txt.


## Fuentes

Parte de esta información ha sido recuperada de los sitios web siguientes:
- [Instalación de Git](https://www.atlassian.com/es/git/tutorials/install-git)
- [How to: Clone GIT Repo Using Personal Access Token](https://www.shanebart.com/clone-repo-using-token/)
- [¿Qué es GITHUB y para qué sirve?](https://www.webempresa.com/hosting/que-es-github.html)
- [Git Checkout](https://www.atlassian.com/es/git/tutorials/using-branches/git-checkout)
- [What is a Git HEAD?](https://careerkarma.com/blog/what-is-a-git-head/)
- [git pull](https://www.atlassian.com/es/git/tutorials/syncing/git-pull)

