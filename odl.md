*nano /etc/ssh/sshd_config
*  PermitRootLogin yes (por defecto pone without-password)
*systemctl start ssh

add-apt-repository ppa:webupd8team/java

*apt-get install openjdk-8-jdk curl
*nano ~/.bashrc 
*  export JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64" (Escribimos esto al final del documento, asegurar la ruta antes de poenrla)
*. ~/.bashrc 
*echo $JAVA_HOME 

Vamos a la página oficial de OpenDaylight y descargamos el archivo TAR de la versión Lithium
https://nexus.opendaylight.org/content/repositories/public/org/opendaylight/integration/distribution-karaf/0.3.0-Lithium/
*mv /home/barbara/Descargas/distribution-karaf-0.3.0-Lithium.tar.gz /root/
*tar -xzf distribution-karaf-0.3.0-Lithium.tar.gz
*ifconfig (Mirar la IP)
*passwd (Cambiar la contraseña)
curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -

*cd distribution-karaf-10.2.0
*./bin/karaf
*feature:install odl-restconf-all odl-l2switch-all odl-mdsal-all odl-dlux-all odl-openflowplugin-all odl-yangtools-common

*Vamos al navegador y ponemos: localhost:8181/index.html
*La usuario y contraseña es admin

mn --custom mininet/custom/tfg.py --topo tfg --controller remote,ip=192.168.2.X,port=6633
pingall

