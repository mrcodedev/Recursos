# Github
![](https://github.com/mrcodedev/Recursos/blob/master/github/img/logogithub.png)

Guía esencial de comandos básicos para empezar con github (desde consola y con git).

# Comandos básicos para iniciarse en git
Para empezar a crear un proyecto debemos de realizar estos pasos (antes debemos de tener instalado git)...

Primero podemos crear un archivo README.md donde va a ir información sobre el proyecto. Para dejarlo más bonito utilizaremos MarkDown.

Nos vamos a la carpeta del proyecto y ponemos lo siguiente:
```
git init
```

Podemos añadir todos los archivos que tengamos (sólo identificará los nuevos) o individuales.

**Individual**
```
git add README.md
```

**Todos**
```
git add .
```

Después debemos de hacer un commit con un mensaje:

```
git commit -m "Hemos añadido el archivo README.MD"
```

Como es la primera vez y no está aún el proyecto enlazado con el repositorio lo enlazamos:

```
git remote add origin https://github.com/mrcodedev/Repositorio.git
```

Y ya después para acabar debemos de subirlo a Github:
```
git push -u origin master
```

## Status de los archivos
Para saber en que status están nuestros archivos debemos de poner lo siguiente:
```
git status
```

## Subir proyecto hecho

Si tenemos un proyecto hecho sólo tenemos que hacer estos pasos:
```
git add .
git commit -m "comentario"
git push
```

Si no funciona el push hacer esto

```
git push -f origin master.
```

Importante **siempre** de utilizar los tres comandos, o no vas a poder hacer nada.

Para aprender como funciona Git puedes hacer el siguiente tutorial: https://try.github.io/levels/1/challenges/1

## Ignorar archivos o carpetas
Para ignorar archivos o carpetas que tengamos, sólo debemos de insertar un archivo llamado .gitignore en la raíz de nuestro proyecto y añadir carpetas o archivos. Un ejemplo sería este:

```
img/*
index.php
.gitignore
src/thumbs.dll
```
En windows desde el explorador no te va a dejar crear este archivo, crealo desde otro sitio y después editalo.


## Repositorio Github sin los archivos excluidos
Si alguna vez hemos trackeado archivos y lo hemos subido a nuestro repositorio de Github, podemos hacer que los borre del repositorio de la siguiente manera: 

```
git rm --cached [filenames]
git commit -m 'Remove the now ignored directory "some-directory"'
git push origin master
```

## Modificar el mensaje del último commit
Para modificar un mensaje de nuestro último commit debemos de usar este comando:
```
git commit --amend -m "your new message"
```

## Clonar repositorio
Para clonar un repositorio haremos lo siguiente:
```
git clone git://github.com/mrcodedev/ejemplo.git
```
Tenemos que tener en cuenta que cuando clonemos un repositorio, se nos va a genererar una carpeta.

License
----
MIT

.
----

**:fire: :fire: Open Source Hell Yeah - OSWeekends (http://osweekends.com/) :fire: :fire:**
