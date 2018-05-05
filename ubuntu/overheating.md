# Ubuntu
![](https://github.com/mrcodedev/Recursos/blob/master/ubuntu/img/logoubuntu.gif?raw=true)



# Prevenir el Overheating en Portátiles Linux
Recursos para reducir temperatura en portátiles que se calientan con una distribución Linux (enfocado principalmente a Ubuntu).
## TLP
Herramienta de administración de energia en Linux. Es una daemon que está preconfigurado para reducir el sobrecalentamiento y mejorar la vida útil de la batería. Sólo se necesita instalar TLP y reiniciar el sistema. Se inicia automáticamente en cada arranque y seguirá ejecutándose en segundo plano.

### Instalar
```
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw
```
### Desinstalar
```
sudo apt-get remove tlp
sudo add-apt-repository --remove ppa:linrunner/tlp
```

## thermald
Desarrollado por la división de código abierto de Intel, Linux Thermal Daemon (thermald), es una herramienta que monitorea y controla la temperatura de la CPU, lo que resulta que se sobrecalienta menos. Thermald está disponible en los repositorios de Ubuntu.

### Instalar
```
sudo apt-get install thermald
```

Debería de estar en otras distribuciones también. Según comenta la gente que thermald y TLP no entran en conflicto entre sí, por lo que puedes instalarlos juntos. Después de la instalación no debes de realizar nada.

Si tu configurar ACPI da algún error o quieres configurar más sensores, puedes editar el archivo de configuración de thermald XML, ubicado en _**/etc/thermald/thermal-conf.xml**_. Si quieres tener más información sobre esto, consulta la página de man de thermal-conf.xml ("_**man thermal-conf.xml**_").

* [Documentación Driver P-State Intel-](https://itsfoss.com/reduce-overheating-laptops-linux/) - Recursos para reducir el calentamiento en portátiles con Linux


License
----
MIT

.
----

**:fire: :fire: Open Source Hell Yeah - OSWeekends (http://osweekends.com/) :fire: :fire:**
