# Serverins
1. Añadir dispositivos
   1a. Arrastra un router modelo 2811 (o similar con 4 interfaces FastEthernet).
   1b. Coloca 4 switches en el área de trabajo.
   1c. Conecta cada switch al router con cable cobre directo.
   1d. Añade 25 PCs a cada switch (total 100 PCs).
   1e. Añade 1 servidor conectado al switch de la Subred A.

2. Configurar el router
   2a. Entra al CLI del router: Router> enable
   2b. Entra a configuración global: Router# configure terminal
   2c. Configura interfaz FastEthernet0/0:
       ip address 192.168.1.1 255.255.255.0
       no shutdown
   2d. Configura interfaz FastEthernet0/1:
       ip address 192.168.2.1 255.255.255.0
       no shutdown
   2e. Configura interfaz FastEthernet0/2:
       ip address 192.168.3.1 255.255.255.0
       no shutdown
   2f. Configura interfaz FastEthernet0/3:
       ip address 192.168.4.1 255.255.255.0
       no shutdown
   2g. Guarda configuración: Router# write memory

3. Configurar el servidor
   3a. Desktop → IP Configuration: IP 192.168.1.2, máscara 255.255.255.0, gateway 192.168.1.1.
   3b. Services → DHCP:
       Pool A: Start 192.168.1.10 – End 192.168.1.254, Gateway 192.168.1.1
       Pool B: Start 192.168.2.10 – End 192.168.2.254, Gateway 192.168.2.1
       Pool C: Start 192.168.3.10 – End 192.168.3.254, Gateway 192.168.3.1
       Pool D: Start 192.168.4.10 – End 192.168.4.254, Gateway 192.168.4.1
   3c. Activa servicios HTTP y DNS si deseas simular web y resolución de nombres.

4. Configurar PCs
   4a. Desktop → IP Configuration → seleccionar DHCP.
   4b. Verificar que reciben IP automática del servidor.

5. Pruebas de conectividad
   5a. Desde un PC de Subred A: ping 192.168.2.10 (PC en Subred B).
   5b. Desde cualquier PC: ping 192.168.1.2 (servidor).
   5c. Abrir navegador en un PC y acceder a http://192.168.1.2.
