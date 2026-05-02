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

## clase 6 Git: Merge, Fetch, Pull, Push

Permite unir dos ramas en una sola, integrando sus commits.

 git merge rama

--no-ff (No Fast Forward)
git merge --no-ff rama

✔️ Fuerza la creación de un commit de merge
✔️ Mantiene el historial de ramas visible
✔️ Evita que Git “salte” directamente sin dejar rastro

💡 Ideal cuando quieres mantener el historial claro (Gitflow) 

### --no-ff (No Fast Forward)
 git merge --no-ff rama

✔️ Fuerza la creación de un commit de merge
✔️ Mantiene el historial de ramas visible
✔️ Evita que Git “salte” directamente sin dejar rastro

💡 Ideal cuando quieres mantener el historial claro (Gitflow)

### ¿Qué es git pull?

Trae los cambios del remoto y los aplica automáticamente.

git pull origin rama

✔️ = fetch + merge
✔️ Actualiza tu rama local

⚠️ Puede generar conflictos si hay cambios incompatibles

### Primera vez (importante)
git push -u origin rama

✔️ Vincula tu rama local con la remota
✔️ Luego puedes usar solo git push

⚠️ Ojo: en tu apunte estaba mal (git pull -u ❌)

### Flujo de trabajo (sin pull requests)

git checkout develop        # Ir a develop
git fetch                   # Ver cambios remotos
git pull origin develop     # Actualizar develop

git merge --no-ff rama      # Fusionar tu rama

# Resolver conflictos manualmente si aparecen

git add .                   # Preparar cambios
git commit                  # Confirmar merge

git branch -D rama          # Eliminar rama local
git push origin develop     # Subir cambios

## clase 7 Pull Requests (PRs)

¿Qué son los Pull Requests?

También llamados PRs, son la forma profesional de trabajar con GitHub.

 -Un Pull Request es una solicitud para:

Revisar cambios
Discutirlos
Y luego fusionarlos (merge) al código principal

 No modificas directamente main o develop, primero pides revisión.

### ¿Cómo crear un PR?
Haces cambios en una rama
Subes tu rama:
git push origin rama
Vas a GitHub
Creas el Pull Request
Esperas revisión y aprobación

### Flujo de trabajo (con Pull Requests)
git checkout develop
git fetch
git pull origin develop

git checkout -b rama        # Crear nueva rama

# Trabajas en tu rama

git push -u origin rama     # Primera vez

# Si develop cambió mientras trabajabas:
git checkout develop
git pull origin develop

git checkout rama
git merge develop           # Actualizar tu rama

# Resolver conflictos si hay

git add .
git commit

git push origin rama        # Subir cambios actualizados

Por qué usar Pull Requests?

Aunque puedes trabajar sin PRs, NO es recomendable en equipo.

### Problemas sin PRs:
Cualquiera puede hacer merge directo ❌
Riesgo de errores ❌
Código sin revisión ❌
Ventajas de los PRs:

✔️ Revisión de código
✔️ Discusión entre el equipo
✔️ Mayor seguridad
✔️ Mejor organización
✔️ Control de quién y qué se integra

💡 Obliga a validar antes de mezclar código

### Protección del repositorio

Para evitar merges directos:

Proteger ramas (branch protection)
Requerir revisiones antes de merge
Limitar permisos

👉 Esto se configura en GitHub

¿Cómo contribuir sin acceso?

Si no eres colaborador:

Haces un fork del repositorio
Trabajas en tu copia
Haces push
Creas un PR al repo original

## Clase 8 Git Stash, borrar ramas y Git Diff

¡Claro que sí! He estructurado y pulido tu contenido para que sea mucho más profesional, fácil de leer y técnicamente preciso. He organizado la información siguiendo el flujo de trabajo lógico de un desarrollador.

### Gestión de Cambios y Conflictos en Git
Es muy común que otro Pull Request (PR) se apruebe y fusione antes que el tuyo. Cuando esto pasa, la rama principal avanza y tu código puede quedar desactualizado o generar conflictos. Aquí te explico cómo manejarlo como un profesional.

### ¿Qué hacer si aprobaron otro PR antes que el mío?
Si el PR de un compañero cambió archivos que tú también tocaste, debes sincronizar tu rama para evitar problemas al integrar. El flujo recomendado es:

Guardar cambios temporales (usando stash).

Actualizar tu rama local con los cambios de la rama principal (main o develop).

Recuperar tus cambios y resolver conflictos si aparecen.

### Git Stash: Tu "baúl" de cambios temporales
 git stash te permite guardar tus modificaciones actuales en una pila provisional sin necesidad de crear un commit. Es ideal para limpiar tu área de trabajo rápidamente.

### ¿Cuándo usarlo?

Para cambiar de rama sin perder lo que llevas hecho.

Para actualizar tu código base (git pull) sin que tus cambios locales estorben.

Para guardar trabajo incompleto de forma segura.

### Comandos esenciales:

 git stash: Guarda los cambios actuales.

 git stash -m "mensaje": Guarda los cambios con una descripción (muy recomendado).

 git stash list: Lista todos los estados guardados.

 git stash pop: Recupera el último stash, lo aplica a tu código y lo elimina de la lista.

### 3. Git Diff: Compara antes de actuar
Antes de hacer un commit o un merge, es vital revisar qué has cambiado exactamente para no subir código basura o errores accidentales.
comando:      funcion: 
git diff,             Muestra cambios locales no preparados (sin git add).
git diff <archivo>    Revisa los cambios de un archivo específico.
git diff --staged     Muestra los cambios ya preparados para el commit.
git diff rama1..rama2 Compara las diferencias totales entre dos ramas.

### Buenas prácticas post-merge
Una vez que tu PR ha sido aprobado y fusionado exitosamente, es importante mantener la higiene del repositorio eliminando las ramas que ya no se usan.

Regla de oro: Un proyecto limpio es un proyecto fácil de mantener.

Borrar rama local:
git branch -d nombre-de-la-rama
(Solo funciona si la rama ya fue fusionada).

Borrar rama remota:
git push origin --delete nombre-de-la-rama

### Resumen del flujo de actualización:
Si necesitas actualizar tu rama porque alguien más mergeó antes:

git stash (Guardas lo tuyo)

git checkout main (Vas a la rama principal)

git pull origin main (Traes lo nuevo)

git checkout tu-rama (Vuelves a tu tarea)

git merge main (Integras lo nuevo en tu rama)

git stash pop (Recuperas tus cambios y resuelves conflictos si existen)
