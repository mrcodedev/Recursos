# Github
![](https://github.com/mrcodedev/Recursos/blob/master/github/img/logogithub.png)

Guía esencial de comandos básicos para empezar con github (desde consola y con git).

# Comandos básicos para mí que soy un paquete
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

## Subir proyecto hecho

Si tenemos un proyecto hecho sólo tenemos que hacer estos pasos:
```
git add .
git commit -m "comentario"
git push
```

Importante **siempre** de utilizar los tres comandos, o no vas a poder hacer nada.

Para aprender como funciona Git puedes hacer el siguiente tutorial: https://try.github.io/levels/1/challenges/1



License
----
MIT

.
----

**:fire: :fire: Open Source Hell Yeah - OSWeekends (http://osweekends.com/) :fire: :fire:**
