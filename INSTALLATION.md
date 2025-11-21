# Manual de como instalar una maquina en IsardVDI

### **Primero de todo tienes que ir a la pagina web official de isardVDI**
![Text alternatiu](foto1.png)

- Luego inicias session con tus credenciales
  ![Text alternatiu](foto2.png)


- Despues de inciar session, haz un click al boton que se llama "Escriptori nou"
![Text alternatiu](foto4.png)

 
 - Ahora pon un nombre de tu gusto a tu maquina y tambien una descripcion si quieres
![Text alternatiu](foto5.png)

-  Luego eliges la maquina que quieres instalar

  ej: Ubuntu, Windows etc...

- Luego de hacer eso bajas al final de la pagina i haces un click al "Crea"

- Despues de esto tendras tu maquina de IsardVDI preparada para utilizar solo tienes que dar un click al iniciar y selecionar SPICE como Visor
![Text alternatiu](foto6.png)

Per instal·lar una pila LAMP a Ubuntu, segueix aquests passos.

# 1. Actualitza el sistema

- sudo apt update && sudo apt upgrade -y

# 2. Instal·la Apache
- sudo apt install apache2 -y
## Activa i inicia el servei:
para activar y iniciar el servei posa aquest comand
- sudo systemctl enable apache2
- sudo systemctl start apache2

# Verifica l’estat:

sudo systemctl status apache2
Visita http://localhost per veure la pàgina per defecte d’Apache.

# 3. Instal·la MySQL
Ubuntu 24.04 ja inclou el paquet mysql-server als repositoris oficials (versió 8.0 o superior):

sudo apt install mysql-server mysql-client -y

# Inicia i habilita el servei:

sudo systemctl enable mysql

sudo systemctl start mysql

# Configura de MySQL:

Accés a la consola de MySQL
sudo mysql
Creació de la base de dades
CREATE DATABASE bbdd;
Creació de l’usuari local
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
GRANT ALL PRIVILEGES ON bbdd.* TO 'usuario'@'localhost';
FLUSH PRIVILEGES;
EXIT;
Nota: Aquest usuari només pot connectar-se des del servidor local (localhost), cosa que és suficient si l’aplicació web i la base de dades estan al mateix servidor.

# 4. Instal·la PHP i extensions comunes

Ubuntu 24.04 inclou PHP 8.3 als repositoris estàndard:

sudo apt install php libapache2-mod-php php-mysql php-curl php-gd php-mbstring php-xml php-zip php-json php-cli -y

# Reinicia Apache per carregar PHP:

sudo systemctl restart apache2
Verifica la versió de PHP:

php -v
# Crea un fitxer de prova:

echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php
Visita http://localhost/info.php per veure la informació de PHP.

Mesura de seguretat: Un cop hagis verificat que funciona, elimina el fitxer:

sudo rm /var/www/html/info.php
Verificació final
La pila LAMP ara hauria d’estar operativa amb:

Apache servint pàgines web.
MySQL preparat per emmagatzemar dades.
PHP processant scripts.
