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
```
git reset --soft HEAD~1
```
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

#### justificacion de inasistencia 
Por un descuido no pude llenar el form del dia martes 21/04, fue por que estaba atendiendo la clase y no me fije el chat del MEET

## CLASE 3
### Guía Rápida: Git y GitHub

Git: Sistema de control de versiones que crea "puntos de guardado" locales.

GitHub: Servidor en la nube para alojar y colaborar en proyectos. Aunque usan Git, no son lo mismo.

#### Autenticación (Recomendado: SSH)
Es preferible usar SSH sobre HTTPS para evitar solicitar credenciales constantemente.

##### Genera tu clave: 
```
ssh-keygen -t ed25519 -C "tu-correo@email.com".
```
##### Copia la clave 
```
(cat ~/.ssh/id_ed25519.pub)
``` 
##### Y agrégala en: 
```
GitHub > Settings > SSH and GPG keys > New SSH Key.
```

#### Comandos Esenciales
##### Clonar un repositorio: 
```
git clone <url-ssh>.
```
##### Conectar repositorio local existente:
```
Bash
git remote add origin <url-ssh>
git branch -M main
git push -u origin main
```
###### [Nota: Requiere git init y un commit previo].

#### Cambiar HTTPS a SSH: 
```
git remote set-url origin <url-ssh>.
```
#### Sincronización:

##### Subir cambios: 
```
git push origin <rama>.
```
##### Traer cambios: 
```
git pull origin <rama>.
```

## CLASE 4
### Guía de Git: Remotos, SSH y Checkout
#### Gestión de Repositorios Remotos
El comando git remote administra las conexiones con repositorios externos:  
##### Visualizar URLs:
```
git remote -v
```
##### Vincular repositorio: 
```
git remote add <apodo> <url>
```
##### Cambiar URL:
```
git remote set-url <apodo> <url>
```
#### Configuración de Múltiples Cuentas SSH
Para manejar varias cuentas (ej. personal y trabajo) sin conflictos, se crean "túneles" específicos:  
##### Generar llave con nombre único: 
```
ssh-keygen -t ed25519 -C "correo@ejemplo.com" -f ~/.ssh/id_nombre
```
##### Archivo config: 
Se define un Host (alias), HostName (github.com), User (siempre git) e IdentityFile (ruta de la llave).  
##### Clonado: 
Es vital usar el Host correcto al clonar: 
```
git clone git@host-personal:usuario/repo.git
```
#### Git Checkout y el Estado "Detached HEAD"
Permite desplazar el puntero HEAD a puntos específicos de la historia
##### Uso: 
Inspeccionar código antiguo, restaurar archivos o experimentar.  
##### Detached HEAD: 
El HEAD apunta a un commit fijo en lugar de a una rama.  
###### Riesgo: 
Los cambios realizados se pierden al volver al presente si no se crea una rama nueva con 
```
git checkout -b <nombre>
```
##### Buenas prácticas: 
Siempre haz commit antes de cambiar de punto en la historia.
## CLASE 5
### Gitflow Básico
#### Gestión de Ramas
Las ramas permiten bifurcar el estado del código para trabajar en paralelo de forma organizada.
```
git branch
```
Lista las ramas y muestra la posición del HEAD.
```
git branch <nombre>
```
Crea una nueva rama desde la posición actual.
```
git branch -D <nombre>
```
Elimina una rama.
```
git checkout <nombre> o git switch <nombre>
```
Cambia a la rama especificada. 
```
git switch
```
Es el comando moderno (desde 2019) especializado exclusivamente en ramas para evitar errores accidentales.
```
git checkout -b <nombre>
```
Crea una rama y se mueve a ella en un solo paso.
#### ¿Qué es Gitflow?
Es un flujo de trabajo que establece reglas para gestionar ramas y versiones de manera ordenada, facilitando la colaboración en equipo.
#### Tipos de Ramas en Gitflow
##### main
Esta presente desde que se crea el repositorio, nunca muere y es donde se guarda el codigo en producción.
##### develop
Nace en el main, no muere nunca y es donde se realiza la pre-produccion y el trabajo diario del equipo.
##### feature/*
Nace y muere en el develop, en esta rama de generan nuevas caracteristicas y/o tareas especificas.
##### release/*
Nace en el develop pero puede morir en el main o en el mismo develop, en esta rama se preparan nuevas versiones y pruebas finales de (QA).
##### hotfix/*
Nace y muere en los mismo lugares que el release, pero sirve solo para parches urgentes que reparen errores em produccion.
## CLASE 6
### Operaciones de Integración y Sincronización
```
git merge
```
Fusiona ramas para unificar el historial de commits.   
```
git merge --no-ff
```
Obliga a crear un commit de fusión, evitando que se pierda el historial visual de la rama aunque esta sea eliminada.  
```
git fetch
``` 
Consulta el repositorio remoto para verificar si existen cambios nuevos en la rama actual o sus dependencias.  
```
git pull origin <rama>
```
Descarga e integra los cambios del repositorio remoto directamente en tu rama local.  
```
git push origin <rama>
```
Sube tus commits locales al servidor remoto.  
```
git push origin <rama> -u
```
Se usa en el primer envío para establecer la relación de seguimiento entre la rama local y la remota.  

#### Flujo de Trabajo Estándar
##### Actualizar base: 
Desde develop, ejecutar fetch y pull.  

##### Trabajo en rama:
Crear/cambiar a tu rama y, si hubo cambios en develop, integrarlos con merge.  

##### Subida: 
Enviar cambios a la rama remota con push.  

##### Integración final:
Regresar a develop, realizar pull para asegurar la última versión y fusionar tu rama con merge --no-ff.  

##### Limpieza: 
Resolver conflictos manualmente si existen, confirmar el commit y eliminar la rama local con git branch -D
## CLASE 7
#### Pull Requests (PRs) y Seguridad
##### Definición: 
Es la metodología profesional para proponer cambios al código base en plataformas como GitHub, permitiendo la revisión antes de la unión definitiva.  
##### Importancia y Seguridad:
Evitan que colaboradores (o agentes externos) integren código malicioso o erróneo sin supervisión.  

Fomentan el debate técnico y la revisión por pares para validar la calidad del código.  

Permiten auditar qué cambios se introducen, quién los hace y por qué.  

##### Flujo de Trabajo con PR:

Actualizar la rama local desde develop.  

Trabajar en la rama propia y sincronizarla con los últimos cambios de develop antes de subirla.  

Realizar 
```
git push origin rama.  
```

Crear formalmente el Pull Request en la interfaz de GitHub para solicitar la revisión y posterior fusión.  

##### Protección del Repositorio: 
Se recomienda configurar reglas en GitHub para limitar la colaboración directa y obligar a que todo cambio pase por una aprobación (review) previa