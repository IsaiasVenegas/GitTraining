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

        git pull dev

Este comando descarga los archivos que se encuentran en la rama **remota** dev **en este momento**. Este proceso es aveces llamado "pulear".

Y ya está! ahora nuestra versión local se encuentra en una nueva rama y está actualizada.

## Tutorial 3: Hacer cambios
Hemos llegado a la parte interesante. Ahora cuentas con dos archivos, uno llamado README.txt y el otro llamado EDITAME.txt, el cuál editaremos (obviamente).

Para no modificar la rama remota dev, probaremos lo aprendido creando una nueva rama siguiendo el tutorial número 3. La rama remota a duplicar será dev y el nombre de la rama local será *tuNombre*.

Hecho esto, abriremos el archivo EDITAME.txt con nuestro editor de código preferido (Bloc de notas, ~~Word~~, Visual Studio Code, etc.) y luego:

1. Al final del archivo, reemplazar los comentarios (las lineas que comienzan con "//") con la información solicitada.
2. Tras esto, abrir el símbolo del sistema y escribir:

        git add EDITAME.txt
        
Este comando le indica a Git que quieres actualizar el archivo EDITAME.txt **remoto** con los cambios que has hecho en la versión **local**. Si se tienen múltiples archivos editados y se desean mencionar todos a la vez, es posible hacerlo en un solo comando utilizando un punto en reemplazo del nombre del archivo. Pero si se tienen múltiples archivos editados y sólo se desean actualizar algunos, se tendrá que escribir uno por uno (o utilizar alguna herramienta disponible en el editor de código utilizado).

3. Luego escribir:

        git commit -m 'Actualizar EDITAME.txt'
        
Para entender este comando es necesario explicar lo que es un *commit*. 

Debes saber que Git es utilizado para controlar las versiones de un código. Esto quiere decir que conserva **todos los cambios que han ocurrido**. En Github, puedes ver la línea temporal de una rama presionando el botón *commits* bajo el botón verde *Code*. Cada elemento presente en la lista es un estado llamado commit y dentro de ellos se encuentran los archivos que fueron actualizados en ese momento. Esto quiere decir, que nuestro **HEAD** de Git no sólo apunta a una rama, sino que también a un commit en específico (sí, también puedes moverte entre commits).

Por lo tanto, este comando toma los archivos añadidos en el paso número 2, los "encapsula" en un commit y le agrega un mensaje personalizado.

4. Finalmente, escribir:

        git push origin tuNombre
     
Dónde origin indica que los cambios serán subidos al repositorio y a la rama *tuNombre*. Ya que esta rama es nueva, el comando también creará su versión remota. Este proceso es a veces llamado "pushear".

Se recomienda encarecidamente no hacer push a la rama principal **main**. Generalmente, esta rama estará protegida y en su lugar se utilizarán ramas secundarias (como dev) para recibir los cambios que luego pasarán a la rama principal, utilizando una herramienta llamada *Pull request*. Esta última se encuentra incluida en Github.

Si deseas practicar más esta parte, repite este tutorial copiando y pegando 2 veces más el último verso del coro y continúa con el paso número 2.

## Problemas usuales
Git y Github no son sólo utilizados para mantener un control de las versiones del código, también son muy útiles para el trabajo colaborativo. El problema es cuando no existe suficiente comunicación entre el equipo.

### No hacer pull antes de hacer push
¿Qué sucedería si tu compañero de trabajo actualiza tu rama remota mientras te encuentras trabajando en ella? pues en teoría nada, pues tu trabajas en la versión local. Pero una vez quieras subir tus cambios te encontrarás con un mensaje indicando que existen cambios en la rama de destino.

Para resolver esto, basta con hacer un pull y luego hacer un push.

### Merge conflict
¿Qué sucedería si tus nuevas lineas de código ocupan la mismas lineas que tu compañero ya editó? (por ejemplo, tu compañero actualizó el EDITAME.txt antes que tú y escribió el último verso mal) pues Git no podrá actualizar tu rama local y te arrojará un mensaje de error, no pudiendo tampoco actualizar la rama remota.

Para solucionar esto, deberás abrir al archivo que cuenta con conflictos y decidir cuál de las dos versiones quieres que se mantengan en el repositorio. En otras palabras, borra las lineas que no estén funcionando.

Se debe tener mucho cuidado para resolver este tipo de conflictos, pues quizás tu compañero resolvió una falla que no se te ha comunicado y tú volverás a agregarla!

## Fuentes

Parte de esta información ha sido recuperada de los sitios web siguientes:
- [Instalación de Git](https://www.atlassian.com/es/git/tutorials/install-git)
- [How to: Clone GIT Repo Using Personal Access Token](https://www.shanebart.com/clone-repo-using-token/)
- [¿Qué es GITHUB y para qué sirve?](https://www.webempresa.com/hosting/que-es-github.html)
- [Git Checkout](https://www.atlassian.com/es/git/tutorials/using-branches/git-checkout)
- [What is a Git HEAD?](https://careerkarma.com/blog/what-is-a-git-head/)
- [git pull](https://www.atlassian.com/es/git/tutorials/syncing/git-pull)

