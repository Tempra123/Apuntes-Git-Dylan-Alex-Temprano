# Trabajo individula 
 Dylan Alex Temprano Villarpando
CEll : 71426919  
##Clase 2
###  States y Commits
 este es una carpeta comun, con la diferencia q git observa tus archivos y los cataloga en untracked y modified 

### Subtitulos 
restaura as su estado original, elimina los cambios, descarta cambios 
...
git restore
...
archivos o carpetas q no deven ser rastreados ni subir al repositorio 
...
git ignore
...
permite seleccionar archivos q se incluiran en el siguiente commit
...
git add <archivo>
...
para guardar todos los cambios realizados con una nota explicativa 
...
git commit -m "mensaje"
...
### Buenas practicas 

Haz commits pequeños y frecuentes, no uno grande con todo.
Cada commit debe representar un cambio específico y completo (una sola cosa bien hecha).
No hagas commits sin sentido cada uno debe tener valor y propósito.
Intenta que el proyecto siempre siga funcionando después de cada commit.

Un buen commit debe ser corto, claro y directo.

 Reglas básicas:
Usa verbos en imperativo:
Add → agregar algo nuevo
Change → modificar algo
Fix → arreglar un error
Remove → eliminar algo
no uses:
punto final
puntos suspensivos
Describe exactamente qué hiciste, sin relleno
usa como maximo 50 caracteres 
usa un prefijo para hacerlos mas semanticos

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

