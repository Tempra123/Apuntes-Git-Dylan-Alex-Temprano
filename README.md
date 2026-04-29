# Trabajo individula 
 Dylan Alex Temprano Villarpando
CEll : 71426919 
## Clase 1 – Introducción a Git
¿Qué es Git?
Git es un Sistema de Control de Versiones Distribuido (VCS).

Permite:

Guardar archivos
Mantener un historial de cambios
Trabajar de manera local sin depender de internet
¿Cómo nació Git?
Git fue creado por Linus Torvalds.

## Configuraciones básicas
Configurar nombre de usuario:

git config --global user.name "Tu Nombre"
Configurar correo:

git config --global user.email "tu@correo.com"
### Archivos importantes en un repositorio
Todo repositorio debería tener:

README.md → Documentación del proyecto
.gitignore → Archivos que Git debe ignorar
## Clase 2 -States y Commits

 Estados de Git
Git maneja 3 estados principales:

### Directorio de trabajo (Working Directory)
Donde editas archivos.
Estados:
Untracked: archivo nuevo sin seguimiento
Modified: archivo ya existente modificado
### Stage Area (Staging)
Área donde eliges qué cambios guardar.
Comandos:
git add <archivo> → agrega uno
git add . → agrega todos
git restore --staged <archivo> → quita del stage
### Repositorio local (Commit)
Donde se guardan los cambios en el historial.
Comandos:
git commit -m "mensaje"
git reset --soft HEAD~1 → deshacer último commit
### Otros comandos importantes
git restore <archivo> → vuelve al estado original (borra cambios)
.gitignore → evita que Git rastree archivos
 ### Buenas practicas 
Hacer commits pequeños (atómicos)
Usar mensajes claros:
Verbos: Add, Fix, Change, Remove
Máximo ~50 caracteres

### Escribe buenos commits
Prefijos:
feat: para una nueva característica para el usuario.
fix: para un bug que afecta al usuario.
perf: para cambios que mejoran el rendimiento del sitio.
build: para cambios en el sistema de build, tareas de despliegue o instalación.
ci: para cambios en la integración continua.
docs: para cambios en la documentación.
refactor: para refactorización del código como cambios de nombre de variables o funciones.
style: para cambios de formato, tabulaciones, espacios o puntos y coma, etc; no afectan al
usuario.
test: para tests o refactorización de uno ya existente.

## clase 3 -GitHub y SSH

## Git vs GitHub
Git → sistema de control de versiones
GitHub → plataforma en la nube para alojar repositorios
## SSH vs HTTPS
HTTPS → pide contraseña/token siempre
SSH → usa claves, más cómodo
recomendacio: usar SSH

## Configurar SSH
Generar clave:
 ssh-keygen -t ed25519 -C "tu-email"
Copiar:
 cat ~/.ssh/id_ed25519.pub
Pegarlo en GitHub (Settings → SSH Keys)
Verificar:
 ssh -T git@github.com
## Trabajar con repositorios
Crear repo en GitHub
Conectar repo local:
 git remote add origin <url>
 git branch -M main 
 git push -u origin main

## Comandos clave
Clonar:
git clone <url>
Subir cambios:
git push origin <rama>
Bajar cambios:
git pull origin <rama>
## Clase 4

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

## Clase 5 RAMAS Y GITFLOW BÁSICO 

¿QUÉ SON LAS RAMAS?

Las ramas son una de las principales utilidades que
disponemos en Git para llevar un mejor control del código.

### Comandos básicos de ramas
Ver ramas :
git branch
🌱 Crear rama:
git branch nombre-rama
❌ Eliminar rama:
git branch -D nombre-rama
🔄 Cambiar de rama:
git checkout nombre-rama
👉 O crear y cambiar al mismo tiempo:
git checkout -b nombre-rama

### Git Checkout vs Git Switch
git checkout → hace muchas cosas (ramas, commits, archivos)
git switch → solo para ramas (más seguro y moderno)
 
### Gitflow básico
🧠 ¿Qué es?

Es una forma ordenada de trabajar con ramas en equipo.

👉 Sin Gitflow:

Todo desordenado 😵

👉 Con Gitflow:

Todo organizado 😎
🌳 Ramas principales
🟢 main
Código en producción
Lo que ya funciona
🟡 develop
Donde se trabaja normalmente
Base de nuevas funcionalidades
🔧 Ramas de apoyo
🔹 feature/*
Para nuevas funcionalidades
Nacen de develop
Vuelven a develop 

