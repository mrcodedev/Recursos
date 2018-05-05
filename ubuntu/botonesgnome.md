# Ubuntu
![](https://github.com/mrcodedev/Recursos/blob/master/ubuntu/img/logoubuntu.gif?raw=true)



# Cambiar de posición los botones de GNOME de la ventana en consola
Para cambiar los botones de sitio en GNOME mediante la consola (se puede hacer facilmente en los ajustes de sistema si no recuerdo), se debe de poner el siguiente comando:

```
gsettings set org.gnome.desktop.wm.preferences button-layout 'close,maximize,minimize:'
```

Para revertirlo: 

```
gsettings set org.gnome.desktop.wm.preferences button-layout ':close,maximize,minimize'
```


License
----
MIT

.
----

**:fire: :fire: Open Source Hell Yeah - OSWeekends (http://osweekends.com/) :fire: :fire:**
