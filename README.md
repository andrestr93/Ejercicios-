# Ejercicios-

# **LINUX FSTAB Y CRONTAB**
## **<span style="color:#68BCFF;">INDICE</span>**
* **[1. FSTAB](#1-fstab)**
    * **[1.1 Crear particiones al primer disco duro](#11-crear-particiones-al-primer-disco-duro)**  
    * **[1.2 Crear particiones al segundo disco duro](#12-crear-particiones-al-segundo-disco-duro)**
    * **[2 Crear montaje de los discos duros](#2-crear-montaje-de-los-discos-duros)**
* **[2. CRONTAB](#2-crontab)**
## **1. FSTAB**
### **1.1 Crear particiones al primer disco duro**
  1. Comprobamos los discos que tenemos conectados con el siguiente comando:  
    `sudo fdisk -l`  
      ~~~
      administrador@ubuntu:~$ sudo fdisk -l
      Disk /dev/sda: 8 GiB, 8589934592 bytes, 16777216 sectors
      Units: sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disklabel type: dos
      Disk identifier: 0x84ddb02c

      Disposit.  Inicio   Start    Final Sectores  Size Id Tipo
      /dev/sda1  *         2048   999423   997376  487M 83 Linux
      /dev/sda2         1001470 16775167 15773698  7,5G  5 Extendida
      /dev/sda5         1001472 16775167 15773696  7,5G 8e Linux LVM


      Disk /dev/sdb: 2 GiB, 2147483648 bytes, 4194304 sectors
      Units: sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disklabel type: dos
      Disk identifier: 0xa2bb358b


      Disk /dev/sdc: 3 GiB, 3221225472 bytes, 6291456 sectors
      Units: sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disklabel type: dos
      Disk identifier: 0xe1fe700b


      Disk /dev/mapper/ubuntu--vg-root: 6,5 GiB, 7000293376 bytes, 13672448 sectors
      Units: sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes


      Disk /dev/mapper/ubuntu--vg-swap_1: 1 GiB, 1073741824 bytes, 2097152 sectors
      Units: sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      ~~~
  2. Accedemos al disco duro que se desa crear la particiones:  
    `sudo fdisk /dev/sdb`
  3. Una vez estemos aquí creamos la tabla de particiones pulsando la `o`
  4. Una vez creada la tabla de particiones crearemos las particiones con la tecla `n`
      1. Pulsaremos la `p` para indicar particion primaria
      2. Seleccionamos la primera particion con el `1`
      3. Pulsamos `intro` para que coja automaticamente el sector de inicio
      4. Introducimos hasta que sector quiere la particion en mi caso `2050000` es aproximadamente 1 GB
  5. Creamos otra particion con la tecla `n`
      1. Pulsaremos la `p` para indicar particion primaria
      2. Seleccionamos la segunda particion con el `2`
      3. Pulsamos `intro` para que coja automaticamente el sector de inicio
      4. Pulsamos `intro` para que coja lo que queda deL disco
  6. Ahora vamos ha cambiar el tipo de la 2 particion a FAT32 para ello pulsamos `t`
      1. Seleccionamos la particion 2 pulsando la tecla `2`
      * Por defecto el tipo de particion es linux por eso no modificamos el primero
      * podemos mostrar todos los tipos de particiones que hay con la tecla `L`
          ~~~
          0  Vacía           24  DOS de NEC      81  Minix / Linux a bf  Solaris
          1  FAT12           27  WinRE NTFS ocul 82  Linux swap / So c1  DRDOS/sec (FAT-
          2  XENIX root      39  Plan 9          83  Linux           c4  DRDOS/sec (FAT-
          3  XENIX usr       3c  PartitionMagic  84  OS/2 hidden or  c6  DRDOS/sec (FAT-
          4  FAT16 <32M      40  Venix 80286     85  Linux extendida c7  Syrinx
          5  Extendida       41  PPC PReP Boot   86  Conjunto de vol da  Datos sin SF
          6  FAT16           42  SFS             87  Conjunto de vol db  CP/M / CTOS / .
          7  HPFS/NTFS/exFAT 4d  QNX4.x          88  Linux plaintext de  Utilidad Dell
          8  AIX             4e  QNX4.x segunda  8e  Linux LVM       df  BootIt
          9  AIX arrancable  4f  QNX4.x tercera  93  Amoeba          e1  DOS access
          a  Gestor de arran 50  OnTrack DM      94  Amoeba BBT      e3  DOS R/O
          b  W95 FAT32       51  OnTrack DM6 Aux 9f  BSD/OS          e4  SpeedStor
          c  W95 FAT32 (LBA) 52  CP/M            a0  Hibernación de  ea  Rufus alignment
          e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a5  FreeBSD         eb  BeOS fs
          f  W95 Ext'd (LBA) 54  OnTrackDM6      a6  OpenBSD         ee  GPT
          10  OPUS            55  EZ-Drive        a7  NeXTSTEP        ef  EFI (FAT-12/16/
          11  FAT12 oculta    56  Golden Bow      a8  UFS de Darwin   f0  inicio Linux/PA
          12  Compaq diagnost 5c  Priam Edisk     a9  NetBSD          f1  SpeedStor
          14  FAT16 oculta <3 61  SpeedStor       ab  arranque de Dar f4  SpeedStor
          16  FAT16 oculta    63  GNU HURD o SysV af  HFS / HFS+      f2  DOS secondary
          17  HPFS/NTFS ocult 64  Novell Netware  b7  BSDI fs         fb  VMFS de VMware
          18  SmartSleep de A 65  Novell Netware  b8  BSDI swap       fc  VMKCORE de VMwa
          1b  FAT32 de W95 oc 70  DiskSecure Mult bb  Boot Wizard hid fd  Linux raid auto
          1c  FAT32 de W95 (L 75  PC/IX           bc  Acronis FAT32 L fe  LANstep
          1e  FAT16 de W95 (L 80  Minix antiguo   be  arranque de Sol ff  BBT
          ~~~
      2. En el caso de escoger fat32 introducimos `b`
  7. Nos salimos guardamos y escribimos los datos introduciendo la `w`
  8. Para completar el formato de la primera particion introducimos:  
    `sudo mkfs.ext4 /dev/sdb1`
  9. Para completar el formato de la segunda particion introducimos:   
    `sudo mkfs.fat /dev/sdb2`

### **1.2 Crear particiones al segundo disco duro**
  1. Comprobamos los discos que tenemos conectados con el siguiente comando:  
    `sudo fdisk -l`  

  2. Accedemos al disco duro que se desa crear la particiones:  
    `sudo fdisk /dev/sdc`
  3. Una vez estemos aquí creamos la tabla de particiones pulsando la `o`
  4. Una vez creada la tabla de particiones crearemos las particiones con la tecla `n`
      1. Pulsaremos la `p` para indicar particion primaria
      2. Seleccionamos la primera particion con el `1`
      3. Pulsamos `intro` para que coja automaticamente el sector de inicio
      4. Introducimos hasta que sector quiere la particion en mi caso `2050000` es aproximadamente 1 GB
  5. Creamos otra particion con la tecla `n`
      1. Pulsaremos la `p` para indicar particion primaria
      2. Seleccionamos la segunda particion con el `2`
      3. Pulsamos `intro` para que coja automaticamente el sector de inicio
      4. Introducimos hasta que sector quiere la particion en mi caso `4100000` es aproximadamente OTRO 1 GB
  6. Creamos otra particion con la tecla `n`
      1. Pulsaremos la `p` para indicar particion primaria
      2. Seleccionamos la tercera particion con el `3`
      3. Pulsamos `intro` para que coja automaticamente el sector de inicio
      4. Pulsamos `intro` para que coja lo que queda deL disco
  7. Ahora vamos ha cambiar el tipo de la 2 particion a NTFS para ello pulsamos `t`
      1. Seleccionamos la particion 2 pulsando la tecla `2`
      * podemos mostrar todos los tipos de particiones que hay con la tecla `L`

      2. En el caso de escoger NTFS introducimos `7`
  8. Ahora vamos ha cambiar el tipo de la 3 particion a FAT32 para ello pulsamos `t`
      1. Seleccionamos la particion 3 pulsando la tecla `3`
      * podemos mostrar todos los tipos de particiones que hay con la tecla `L`

      2. En el caso de escoger fat32 introducimos `b`
  9. Nos salimos guardamos y escribimos los datos introduciendo la `w`
  10. Para completar el formato de la primera particion introducimos:  
    `sudo mkfs.ext4 /dev/sdc1`
  11. Para completar el formato de la segunda particion introducimos:   
    `sudo mkfs.ntfs /dev/sdc2`
  12. Para completar el formato de la tercera particion introducimos:   
    `sudo mkfs.fat /dev/sdc3`

### **2 Crear montaje de los discos duros**
  1. Para ello vamos a configurar el fichero:  
    `sudo nano /etc/fstab`
      ~~~
      # /etc/fstab: static file system information.
      #
      # Use 'blkid' to print the universally unique identifier for a
      # device; this may be used with UUID= as a more robust way to name devices
      # that works even if disks are added and removed. See fstab(5).
      #
      # <file system> <mount point>   <type>  <options>       <dump>  <pass>
      /dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
      # /boot was on /dev/sda1 during installation
      UUID=c29a4022-e6c4-429c-84e5-243099e9b66f /boot           ext2    defaults        0       2
      /dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
      #Disco 2
      UUID=c3e52e7b-dd1a-45d5-bbef-492582f2cedc       /media/sdb1     ext4    defaults,noauto         0       0
      UUID=9BED-B5F0  /media/sdb2     vfat    defaults,noauto 0       0

      #Disco 3
      /dev/sdc1       /media/sdc1     ext4    defaults        0       0
      /dev/sdc2       /media/sdc2     ntfs    defaults        0       0
      /dev/sdc3       /media/sdc3     vfat    defaults        0       0
      ~~~
  * parametros del archivo de configuracion
      - file system: Define la partición o dispositivo de almacenamiento para ser montado.
      - mount point: Indica a la orden mount el punto de montaje donde la partición (file system) será montada.  
      - type: Indica el tipo de sistema de archivos de la partición o dispositivo de almacenamiento para ser montado. Hay muchos sistemas de archivos diferentes que son compatibles como, por ejemplo: p `ext2`, `ext3`, `ext4`, `reiserfs`, `xfs`, `jfs`, `smbfs`, `iso9660`, `vfat`, `ntfs`, `swap` y `auto`. El type auto permite a la orden mount determinar qué tipo de sistema de archivos se utiliza. Esta opción es útil para proporcionar soporte a unidades ópticas (CD/DVD).
      - options: Indica las opciones de montaje que la orden mount utilizará para montar el sistema de archivos. Algunas de las opciones más comunes son:
          - defaults: utiliza las opciones por defecto, que son `rw, suid, dev, exec, auto, nouser, async`.
          - `rw`: monta el filesystem como lectura/escritura.
          - `ro`: monta el filesystem como de sólo lectura.
          - `suid`: Permite las operaciones de suid, y sgid bits. Se utiliza principalmente para permitir los usuarios comunes ejecutar binarios con privilegios concedidos temporalmente con el fin de realizar una tarea específica.
          - `nosuid`: Bloquea el funcionamiento de suid, y sgid bits
          - `dev`: Intérprete de los dispositivos especiales o de bloque del sistema de archivos.
          - `nodev`: Impide la interpretación de los dispositivos especiales o de bloques del sistema de archivos.
          - `exec`: Permite la ejecución de binarios residentes en el sistema de archivos.
          - `noexec`: No permite la ejecución de binarios que se encuentren en el sistema de archivos.
          - `auto`: el sistema de archivos será montado automáticamente al iniciar el sistema o al ejecutar el comando mount -a.
          - `noauto`: debe ser montado explícitamente.
          - `user`: permite que cualquier usuario pueda montar el filesystem.
          - `nouser`: especifica que el filesystem sólo puede ser montado por el usuario root y no por un usuario común.
          - `async`: las escrituras al filesystem se demoran, es decir que no se hacen en el momento sino que se hacen varias escrituras juntas. Esto da un mayor rendimiento, aunque si el sistema se cuelga, apaga o el filesystem se desmonta, los datos se pederán si aún no han sido escritos.
          - `sync`: todas las escrituras al filesystem se hacen en el momento. Esto da mayor seguridad a los datos pero un menor rendimiento.
      - dump: Utilizado por el programa dump para decidir cuándo hacer una copia de seguridad. Dump comprueba la entrada en el archivo fstab y el número de la misma le indica si un sistema de archivos debe ser respaldado o no. La entradas posibles son `0` y `1`. Si es `0`, dump ignorará el sistema de archivos, mientras que si el valor es `1`, dump hará una copia de seguridad. La mayoría de los usuarios no tendrán dump instalado, por lo que deben poner el valor 0 para la entrada <dump>.
      - pass: Utilizado por fsck para decidir el orden en el que los sistemas de archivos serán comprobados. Las entradas posibles son `0`, `1` y `2`. El sistema de archivos raíz («root») debe tener la más alta prioridad: `1` -todos los demás sistemas de archivos que desea comprobar deben tener un `2`-. La utilidad fsck no comprobará los sistemas de archivos que vengan ajustados con un valor `0` en `<pass>`.
      - [more](https://wiki.archlinux.org/index.php/Fstab_(Espa%C3%B1ol))
  2. Para montar automaticamente las particiones podemos reiniciar `sudo reboot` o con este comando `sudo mount -a`.

  3. Para montar manualmente usaremos el siguiente comando `sudo mount /dev/sdb1 /media/sdb1` y para la segunda particion `sudo mount /dev/sdb2 /media/sdb2` Crear Las carpetas donde deseais montarlos con `mkdir`.
  4. Para ver donde estan montados o la uuid de las particiones y si estan montadas o no con el siguiente comando  
  `sudo blkid -o list`.

## **2. CRONTAB**
  Accedemos la fichero mediante este comando  
  `sudo nano /etc/crontab`
  * Parametros del crontab
      * `m`: Minutos del 0 a 59
      * `h`: Horas del 0 a 23
      * `dom`: Día del mes del 1 a 31
      * `mon`: Mes del 1 a 12
      * `dow`: Día de la semana del 0 a 6, siendo 0 el domingo.  
        Si se deja un asterisco, quiere decir "cada" minuto, hora, día de mes, mes o día de la semana.
      * `user`: El usuario root ejecuta este comando.
      * `command`: Instrucciones a realizar al activarse
      * Una vez editado el fichero lo reiniciaremos con `sudo /etc/init.d/cron restart` o `sudo /etc/init.d/cron reload`
  - Cada hora en punto ejecutamos la sincronización horaria y mandamos la salida a /dev/null/  
      Instalamos ntp `sudo apt-get install ntp`  
      `00 *    * * *   root    ntpdate -u hora.rediris.es >> /dev/null`  

  - Programar un trabajo (A) para ejecutarse en el minuto 30 de cada hora de cada día.  
    `30 *    * * *   root    echo "A" >> /etc/trabajo ; date +%H:%M >> /etc/trabajo`  

  - Programar un trabajo (B) para ejecutarse cada día a las 20:30h.  
    `30 20  * * *   root    echo "B" >> /etc/trabajo ; date +%H:%M >> /etc/trabajo`  

  - Programar un trabajo (C) para ejecutarse de lunes a viernes a las 20:30h.  
    `30 20   * * 1,2,3,4,5   root    echo "C" >> /etc/trabajo ; date +%H:%M >> /etc/trabajo`  

  - Programar un trabajo (D) para ejecutarse los martes y los jueves a las 20:30h.  
    `30 20   * * 2,4   root    echo "D" >> /etc/trabajo ; date +%H:%M >> /etc/trabajo`  

  - Programar un trabajo (E) para ejecutarse los días 10 y 20 de todos los meses a las 20:30h.  
    `30 20   10,20 * *   root    echo "E" >> /etc/trabajo ; date +%H:%M >> /etc/trabajo`  

  - Programar un trabajo (F) para ejecutarse cada 15 minutos.  
    `00,15,30,45 *   * * *   root    echo "F" >> /etc/trabajo ; date +%H:%M >> /etc/trabajo`  

  - Programar un trabajo (G) para ejecutarse cada día a las 00:00h.  
    `00 00   * * *   root    echo "G" >> /etc/trabajo ; date +%H:%M >> /etc/trabajo`  

  - Programar un trabajo (H) para ejecutarse cada primer día de mes a las 00:00h.   
    `00 00   1 * *   root    echo "H" >> /etc/trabajo ; date +%H:%M >> /etc/trabajo`  

El trabajo que se debe ejecutar es:  
Añadir al fichero /etc/trabajos (no existe hay que crearlo) el código del trabajo y la hora de ejecución.

**3. CLUSTER**
![](https://github.com/xus17/cluster-fstab/raw/master/Captura%20de%20pantalla%20(226).png)
![](https://github.com/xus17/cluster-fstab/raw/master/Captura%20de%20pantalla(199).jpeg)
**COMANDOS DE COMPROBACIÓN Y RECONOCIMENTO
cat clusterhosts
recon -v clusterhosts**



![](https://github.com/xus17/cluster-fstab/raw/master/Cpatura%20de%20pantalla(200).jpeg)
![](https://github.com/xus17/cluster-fstab/raw/master/Captura%20de%20pantalla(201).JPG)





