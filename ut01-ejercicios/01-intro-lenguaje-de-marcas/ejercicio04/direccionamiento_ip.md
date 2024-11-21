# Direccionamiento IP
El direccionamiento IP es un componente esencial en las redes de computadoras, permitiendo la indentificación de dispositivos y la correcta entrega de datos. Las direcciones IP se dividen en clases y tienes rangos específicos según su uso.
## Clases de direcciones IP
A continuación, se muestra la tabla con las clases de direcciones IP, sus rangos, máscaras de subred, rangos privados y el número de hosts disponibles por cada clase:

| __Clase__| __Rango de Direcciones__| __Máscara de Subred__| __Rango Privado__ | __Número de Hosts__ |
|----------|-----------|-----------|-----------|-----------|
|A|0.0.0.0 - 127.255.255.255|255.0.0.0|10.0.0.0 - 10.255.255.255|16,777,214|
|B|128.0.0.0 - 191.255.255.255|255.255.0.0|172.16.0.0 - 172.31.255.255|254|
|C|192.0.0.0 - 223.255.255.255|255.255.255.0|192.168.0.0 - 192.168.255.255|254|
|D|224.0.0.0 - 239.255.255.255|No aplica|No aplica|Multicast (No asginado)|
|E|240.0.0.0 - 255.255.255.255|No aplica|No aplica|Reservado (No asginado)|
## Descripción de las clases 
* __Clase A:__ Usada principalmente para grandes redes, como empresas multinacionales. Soporta un gran número de dispositivos
* __Clase B:__ Orienta a redes medianas, como instrucciones educativas o grandes empresas.
* __Clase C:__ Utilizada para redes pequeñas, como oficinas o redes domésticas
* __Clase D:__ Reservada para multicast
* __Clase E:__ Reservada para usos futuros o experimentales

Para más información sobre redes y direcciones IP, consulta la documentación y recursos adicionales disponibles en el material de estudio.