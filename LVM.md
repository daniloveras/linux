


Rode os seguintes comandos para expandir os espaço no volume físico do sistema operacional fazendo o rescan do SCSI BUS e assim adicionando SCSI Device.

# ls /sys/class/scsi_host/

# echo "- - -" > /sys/class/scsi_host/host0/scan

# echo "- - -" > /sys/class/scsi_host/host1/scan 

# echo "- - -" > /sys/class/scsi_host/host2/scan
   
Verifique os nomes dos dispositivos SCSI e então faça o rescan destes dispositivos usando os seguintes comandos:

# ls /sys/class/scsi_device/

# echo 1 > /sys/class/scsi_device/0\:0\:0\:0/device/rescan

# echo 1 > /sys/class/scsi_device/2\:0\:0\:0/device/rescan

Isto irá realizar o rescan dos dispositivos SCSI e o tamanho do disco será aumentado para a máquina.


Criando Volume Físico.

Execute o comando 'partprobe' para que as tabelas de partição fiquem prontas e aptas para criar um novo volume.

 
# partprobe

Para criar um novo volume execute o seguinte comando:

# pvcreate /dev/sda3

Para verificar se o novo volume foi criado execute o seguinte comando:

# pvdisplay


# vgextend centos /dev/sda3

Extendendo o volume lógico:

Execute o seguinte comando para aumentar o espaço em disco utilizando o espaço livre:

#  lvextend -l +100%FREE /dev/mapper/centos-root


Depois que você conseguir  estender a partição com sucesso execute os seguinte comando para aumentar o tamanho do seu volume lógico:

Para partições XFS:

xfs_growfs /dev/mapper/centos-root

Para partições EXT4:

resize2fs /dev/mapper/centos-root













