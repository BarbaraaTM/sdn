# Instalación de Mininet en Ubuntu

apt-get update && upgrade
apt-get install git
apt-get install --reinstall ca-certificates (Reinstalar certificados ssl)
git clone https://github.com/mininet/mininet

mininet/util/install.sh -a
sudo mn --switch ovsbr --test pingall

sudo mn (Esto crea una red con dos hosts, un controlador y un switch)

# Comandos de Mininet

nodes (Nos muestra los nodos que hay conectados en la red)
net (Nos muestra las conexiones y los puertos)
dump (Nos muestra las IP)
h1 ps -a (Lista de procesos del host 1)
h1 ping -c 1 h2 (Ping de un host a otro)
pingall (Muestra el resultado de los ping entre todos los hosts)
link s1 h1 down (Deshabilita el enlace entre el switch y el host)
link s1 h1 up (Habilita el enlace entre el switch y el host)
iperf (Prueba de ancho de banda)
exit (Salir de Mininet)
xterm h1 (Abrir la consola del host)

## Topologías

sudo mn --topo linear,4
sudo mn --topo tree,depth=2

# Abrir Miniedit

sudo mn
cd mininet/examples
./miniedit.py

Creamos la topología que deseemos, para guardar vamos a File -> Export Level 2 Script y lo guardamos en ~/mininet/custom con el nombre que deseemos con .py
cd ~/mininet/custom
sudo python topologia.py

Para comprobar y ver los paquetes echo, abrimos la terminal de dos hosts con el comando xterm. En un dejamos el ping mandando paquetes y en el otro abrimos WireShark con el comando wireshark &
Seleccionamos la interfaz y le damos a Start. 




























