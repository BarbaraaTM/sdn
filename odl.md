Vamos a la página oficial de OpenDaylight y descargamos el archivo ZIP de la versión Potassium-SR2
https://docs.opendaylight.org/en/latest/downloads.html

sudo apt-get install bash-completion software-properties-common python-software-properties sudo curl ssh git (Aceptamos los términos de Oracle)

sudo nano /etc/ssh/sshd_config
  PermitRootLogin yes (por defecto pone without-password)
sudo systemctl start ssh

sudo apt-get install openjdk-11-jdk
nano ~/.bashrc 
  export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64 (Escribimos esto al final del documento, asegurar la ruta antes de poenrla)
. ~/.bashrc 
echo $JAVA_HOME 


cd
wget https://nexus.opendaylight.org/content/repositories/public/org/opendaylight/integration/distribution-karaf/10.2.0/distribution-karaf-10.2.0.tar.gz
tar -xzf distribution-karaf-10.2.0.tar.gz
ifconfig (Mirar la IP)
passwd (Cambiar la contraseña)

cd distribution-karaf-10.2.0
./bin/karaf
feature:install odl-restconf-all odl-l2switch-all odl-mdsal-all odl-dlux-all odl-openflowplugin-all odl-yangtools-common

Vamos al navegador y ponemos: localhost:8181/index.html
La usuario y contraseña es admin

sudo mn --controller=remote,ip=127.0.0.1,port=6633
pingall

