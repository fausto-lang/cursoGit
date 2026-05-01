# TRABAJO_INDIVIDUAL

FAUSTO JAFETH VILCHES MENDIETA 

## CLASE 1

### ¿Qué es GIT? 

GIT es un sistema de control que permite guardar archivos y las diferentes versiones de estas a lo largo del tiempo de manera local.

### ¿Cómo nacio GIT?

Git nació en 2005 como una respuesta a las limitaciones de otros sistemas de control de versiones, como BitKeeper. Fue creado por Linus Torvalds, el creador del kernel de Linux, y se desarrolló rápidamente para ofrecer un sistema distribuido, eficiente y seguro para el desarrollo de software. Desde su lanzamiento, Git ha evolucionado y se ha convertido en el sistema de control de versiones más utilizado en el desarrollo de software moderno.

### ¿Cómo instalar GIT?

Puedes instalas GIT desde cualquier navegador web y los pasos de instalacion sun depende al Sistema Operativo, ya despues para verificar la correcta instalacion se usa en la terminal el siguiente comando: 

```
git --version
```

### Cnfiguraciones Basicas

```
git config --global user.name "Tu Nombre"
git config --global user.email "tu@correo.com"
```

### Archivo que todo GIT debe tener

Un archivo README. md y un archivo .gitignore






## CLASE 2

### STATES EN GIT (ESTADOS EN GIT)

Para entender esto iniciemos desde el punto de vista de que GIT tiene un flujo de trabajo definido dividido en 3 niveles los cuales son:
#### Working Directory (Directorio de Trabajo)

Es donde se pueden hacer modificaciones(eliminar,añadir o escribir más codigo), estos archivos estan de manera "física" en la computadora.
Aqui los archivos estan en modo "Modified"(Modificados) o UNTRACKED(Sin seguimiento), en este modo git sabe que cambiaste algo pero aun no lo tiene "ASEGURADO"

```
git restore <archivo>
```

Esto borra físicamente lo que escribieron

#### Stage Area (Área de Preparación)
Es una zona intermedia, como una "sala de espera" o un borrador antes de confirmar los cambios.
En esta parte se seleciona que cambios se quieren hacer en el siguiente commit.

Usas:
```
git add <archivo>   Agrega el archivo <archivo>, lo hace uno por uno
git add .  Agrega todos los archivos observados por GIT
``` 
para mover tus cambios del Directorio de Trabajo al Stage Area.

#### Local Repository (Repositorio Local)
Se realiza el Commit. Al hacer esto, Git le asigna un ID único (un hash) a ese conjunto de cambios y guarda quién lo hizo, cuándo y por qué.
Usas:
```
git commit -m "mensaje descriptivo"
```
Si quieres deshacer el ultimo commit el comando simple es:
´´´
git reset --soft HEAD~1
´´´
### COMMITS EN GIT

#### Buenas practicas 
Aquí usaremos los commits atómicos. Son una práctica en Git donde cada confirmación (commit) representa un único cambio lógico, pequeño y completo en el código fuente.
Pero esto no significa hacer commits sin sentido
1.Usa verbos imperativos (Add, Change, Fix, Remove)
            Add: Significa que se añade un nuevo archivo.
            Change: Significa que se modifica un archivo existente.
            Fix: Significa que se arregla un bug.
            Remove: Significa que se elimina un archivo existente.
2.No uses punto final ni puntos suspensivos en tus mensajes
            git commit -m “Add new search feature.”  MAL. No uses punto final
            git commit -m “Fix a problem with topbar..” MAL. No uses puntos suspensivos
            git commit -m “Change the default system color” BIEN

3.Usa como máximo 50 caracteres
            Se corto y conciso.
4.Usa un prefijo para tus commits para hacerlos más semánticos
            git commit -m “<tipo de commit>: <descripción>"
            prefijos:
                feat: para una nueva característica para el usuario.
                fix: para un bug que afecta al usuario.
                perf: para cambios que mejoran el rendimiento del sitio.
                build: para cambios en el sistema de build, tareas de despliegue o instalación.
                ci: para cambios en la integración continua.
                docs: para cambios en la documentación.
                refactor: para refactorización del código como cambios de nombre de variables o funciones.
                style: para cambios de formato, tabulaciones, espacios o puntos y coma, etc; no afectan al usuario.
                test: para tests o refactorización de uno ya existente.
            por ejemplo:
                ```
                git commit -m “feat: Add new search feature"
                ```

5.Añade todo el contexto que se necesario en el cuerpo del commit
            
            ```
            git commit
            ```

            prefijo: Titulo de tu commit
            Cuerpo que describe tu commit 

# justificacion de inasistencia 
Por un descuido no pude llenar el form del dia martes 21/04, fue por que estaba atendiendo la clase y no me fije el chat del MEET