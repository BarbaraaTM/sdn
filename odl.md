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




#!/usr/bin/python

from mininet.net import Mininet
from mininet.node import Controller, RemoteController, OVSKernelSwitch, Host
from mininet.cli import CLI
from mininet.link import Intf
from mininet.log import setLogLevel, info

def myNetwork():

	net = Mininet(topo=None,build=False)

	info('*** Agregando controlador\n')
	net.addController(name='c0', controller=RemoteController, ip='192.168.2.10', port=6633)

	info('*** Agregando switches\n')
	s1 = net.addSwitch('s1', cls=OVSKernelSwitch)
  Intf ( 'enp0s8', node=s1 )
	Intf ( 'enp0s9', node=s1 )
	s2 = net.addSwitch('s2', cls=OVSKernelSwitch)
	Intf ( 'enp0s8', node=s2 )
	Intf ( 'enp0s9', node=s2 )

	info('*** Agregando hosts\n')
	h1 = net.addHost('h1', cls=Host, ip='0.0.0.0')
	h2 = net.addHost('h2', cls=Host, ip='0.0.0.0')

	info('*** Agregando links\n')
	net.addLink(h1, s1)
	net.addLink(h2, s2)
	net.addLink(s1, s2)

	info('*** Iniciando la red\n')
	net.start()
	h1.cmdPrint('dhclient '+h1.defaultIntf().name)
	h2.cmdPrint('dhclient '+h2.defaultIntf().name)
	CLI(net)
	net.stop()
if __name__ == '__main__':
	setLogLevel('info')
	myNetwork()
