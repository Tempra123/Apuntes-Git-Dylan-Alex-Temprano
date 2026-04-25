# Trabajo individula 
 Dylan Alex Temprano Villarpando
CEll : 71426919  
##Clase 4

###  REMOTE, SSH MULTIPLE YCHECKOUT

1. Git Remote (conectar con repositorios)

Git por sí solo trabaja localmente, pero con git remote le dices: “¿a dónde voy a enviar o de dónde voy a traer cambios?”

git remote -v → ves a qué repositorio estás conectado
git remote add origin URL → conectas tu repo local con uno en la nube
git remote set-url origin URL → cambias esa conexión

2. SSH y múltiples cuentas

SSH es como una llave segura para conectarte a GitHub sin poner contraseña.

Cada cuenta necesita su propia “llave” Si tienes varias cuentas → necesitas múltiples SSH
Analogía:

cada cuenta = una puerta
cada SSH = una llave distinta

Para evitar conflictos:

creas varias keys
configuras un archivo config
usas alias como github-miname

3. Configuración local vs global
--global → aplica para todos los proyectos
sin --global → solo para ese repo

4. Git Checkout (viajar en el tiempo)

Es el comando para moverte en el historial o entre ramas.

Sirve para:

ver código antiguo
recuperar cosas
probar sin romper nada
cambiar de rama
