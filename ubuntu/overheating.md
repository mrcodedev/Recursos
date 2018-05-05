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

## Intel_PState
intel_pstate es un nuevo controlador de escala de potencia para las CPU Intel modernas (admite procesadores Intel SandyBridge+). Según Arjan van de Ven de Intel, ondemand no debería usarse más y, en cambio, los procesadores Intel modernos deberían usar Intel P-state.

* [Documentación Driver P-State Intel-](https://github.com/mrcodedev/Recursos/blob/master/ubuntu/overheating/intel-pstate.txt) - P-State Text 
* [Discusión Arjan van de Ven de Intel](https://plus.google.com/+TheodoreTso/posts/2vEekAsG2QT) - Link con la converación

El pstate suele estar desactivado y debemos de activarlo. Debemos de editar el archivo de configuración ("_**/etc/default/grub**_") con un editor de texto con root.

```
sudo nano /etc/default/grub
```

Y para "GRUB_CMDLINE_LINUX_DEFAULT =" agrega "intel_pstate = enable", así:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_pstate=enable"
```

Mira que esté bien editado, o Ubuntu no arrancará. No te olvides después de actualizar GRUB.


```
sudo update-grub
```

Reinicia Ubuntu y para verificar que intel_pstate está habilitado, ejecuta el siguiente comando: 

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
```

El anterior comando debe de devolver el "intel_pstate".

Para poder utilizar los comandos "cpupower" debes de instalar "linux-tools-common" y "linux-tools-generic":

```
sudo apt-get install linux-tools-common linux-tools-generic
```

Para ver de otra manera que Intel P-State está habilitado es mediante el siguiente comando:

```
cpupower frequency-info
```

La salida debería de ser algo parecido a esto:

```
analyzing CPU 0:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 0.97 ms.
  hardware limits: 800 MHz - 3.10 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 800 MHz and 3.10 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  boost state support:
    Supported: yes
    Active: yes
    25500 MHz max turbo 4 active cores
    25500 MHz max turbo 3 active cores
    25500 MHz max turbo 2 active cores
    25500 MHz max turbo 1 active cores
```

Si con todo esto no sale habilitado, lo más seguro es que tu CPU no sea compatible con intel_pstate, por lo que deberías de deshabilitarlo del grub (el paso que hicimos antes en /etc/default/grub).

Con intel_pstate, solo hay dos "governadores" cpufreq: performance y powersave (ya no hay ondemand). Puedes alternar manualmente entre los dos intel_pstate "performance" y "powersave" con los siguientes comandos:

**powersave**
```
sudo cpupower frequency-set -g powersave
```

**performance**
```
sudo cpupower frequency-set -g performance
```

Puedes ver que governor se está utilizando en esos instantes con el siguiente comando: 

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

Si quieres que el governor "powersave" esté predeterminado en Ubuntu (haciendo lo de antes se pierde en cada reinicio), primero instala cpufrequtils:

```
sudo apt-get install cpufrequtils
```

Y luego editar /etc/init.d/cpufrequtils y cambiar el GOVERNOR de "ahorro energia (powersave)" GOVERNOR = "powersave". Puedes hacerlo también con el siguiente comando:

```
sudo sed -i 's/^GOVERNOR=.*/GOVERNOR="powersave"/' /etc/init.d/cpufrequtils
```

Para revertir el cambio y poner el governor en predeterminado (que es "ondemand" y no está disponible para Intel P-State) usa el siguiente comando:

```
sudo sed -i 's/^GOVERNOR=.*/GOVERNOR="ondemand"/' /etc/init.d/cpufrequtils
```

## Laptop Mode Tools
Laptop Mode Tools es un paquete de ahorro de energía portátil para sistemas Linux, que permite configurarlo de varias maneras posibles para obtener más duración de la batería. Lo que pasa que **no es compatible con TLP**, así que si instalas este, debes de desinstalar TLP.

```
sudo add-apt-repository ppa:webupd8team/unstable
sudo apt update
sudo apt install laptop-mode-tools
```

También tiene una GUI que se puede configurar fácilmente la herramienta. Puedes iniciar la GUI usando el siguiente comando: 

```
gksu lmt-config-gui
```

## CPUfreq
Con CPUfreq, puede elegir el modo en el que se desea que se ejecute el portátil. Hay tres modos: rendimiento, bajo demanda y ahorro de energía. La ejecución del portátil en modo ahorro de energía reduce el sobrecalentamiento. Para instalar CPUfreq debes usar el siguiente comando:

```
sudo apt install indicator-cpufreq
```

Para configurarlo debes de elegir el modo ahorro en el barra de tareas.

Esta herramienta no entra en conflicto con ninguna de las anteriores mencionadas.

License
----
MIT

.
----

**:fire: :fire: Open Source Hell Yeah - OSWeekends (http://osweekends.com/) :fire: :fire:**
