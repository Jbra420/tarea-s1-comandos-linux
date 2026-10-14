# Tarea autónoma semana 1: Comandos de Linux

## 1. Título
Creación y manipulación de archivos y directorios mediante comandos de Linux en la terminal

## 2. Tiempo de duración
40 minutos

## 3. Fundamentos

La **terminal** (o línea de comandos) es una interfaz basada en texto que permite comunicarse con el sistema operativo escribiendo órdenes, en lugar de usar ventanas y el ratón. El programa que interpreta esas órdenes se llama **shell**; los más comunes son **bash** (por defecto en la mayoría de distribuciones Linux y en Git Bash) y **zsh** (por defecto en macOS). Como macOS y Linux derivan de la familia Unix, comparten casi todos los comandos básicos, por lo que esta práctica puede realizarse en Ubuntu, WSL, Git Bash o la Terminal de Mac.

En Linux todo se organiza en un **sistema de archivos jerárquico** con forma de árbol, que parte de la raíz `/`. Cada usuario tiene un directorio personal (`~`). Para movernos usamos rutas **absolutas** (que empiezan en `/`) o **relativas** (a partir del directorio actual). Los comandos `pwd` (mostrar el directorio actual), `cd` (cambiar de directorio) y `ls` (listar contenido) son la base de la navegación.

Para crear y gestionar la estructura se utilizan:
- `mkdir`: crea directorios.
- `touch`: crea un archivo vacío o actualiza su fecha de modificación.
- `cp`: copia archivos; si el destino tiene otro nombre, la copia queda renombrada.
- `mv`: mueve o renombra archivos y carpetas.
- `rm`: elimina archivos de forma permanente (no pasan a la papelera).
- `rmdir`: elimina un directorio solo si está vacío, lo que evita borrados accidentales.
- `cat`: muestra o concatena el contenido de archivos.
- `echo`: imprime texto en la salida estándar.

Un concepto clave es la **redirección**. Cada programa tiene una entrada estándar (stdin), una salida estándar (stdout) y una salida de errores (stderr). El operador `>` envía la salida de un comando a un archivo **sobrescribiéndolo**, mientras que `>>` **añade** el contenido al final sin borrar lo existente.

Otro concepto fundamental son las **tuberías** (*pipes*), representadas por `|`. Una tubería conecta la salida de un comando con la entrada del siguiente, permitiendo combinar herramientas pequeñas para resolver tareas más complejas, siguiendo la filosofía Unix de "hacer una sola cosa y hacerla bien". Por ejemplo, `history 1 | cat > archivo.txt` toma el historial de comandos y lo guarda en un archivo.

Finalmente, `history` muestra la lista de comandos ejecutados en la sesión, útil para documentar y repetir trabajo. En zsh, `history 1` muestra el historial completo desde el primer comando.

## 4. Conocimientos previos
Para realizar esta práctica el estudiante necesita tener claro los siguientes temas:
- Concepto de sistema operativo y sistema de archivos.
- Uso básico de la terminal (abrir, escribir y ejecutar comandos).
- Rutas absolutas y relativas.
- Conceptos básicos de Git y GitHub (repositorio, commit, push).
- Sintaxis básica de Markdown.

## 5. Objetivos a alcanzar
- Crear una estructura de directorios usando `mkdir`.
- Crear, copiar, renombrar y mover archivos con `touch`, `cp` y `mv`.
- Aplicar redirección (`>` y `>>`) para escribir y añadir contenido a archivos.
- Eliminar archivos y directorios vacíos con `rm` y `rmdir`.
- Utilizar tuberías (`|`) para volcar el historial de comandos a un archivo.
- Documentar la práctica en Markdown y publicarla en un repositorio de GitHub.

## 6. Equipo necesario
- Computador MacBook Air 2020 con macOS.
- Aplicación Terminal (shell zsh).
- Git (Command Line Tools de Xcode).
- Cuenta en GitHub.
- Navegador web.

## 7. Material de apoyo
- Guía de la asignatura.
- Documentación de comandos con `man` (por ejemplo, `man ls`).
- Cheat sheet de comandos Linux.
- Documentación oficial de GitHub.

## 8. Procedimiento

**Paso 1: Ubicarse en el directorio de trabajo y crear la estructura de carpetas**
```bash
cd ~/Desktop
mkdir proyecto_comandos
cd proyecto_comandos
mkdir documentos imagenes scripts
ls
```

**Paso 2: Crear `notas.txt` y agregar tres líneas con `echo`**
```bash
touch documentos/notas.txt
echo "Primera línea: estoy aprendiendo comandos de Linux" > documentos/notas.txt
echo "Segunda línea: mkdir crea carpetas" >> documentos/notas.txt
echo "Tercera línea: cp copia y mv mueve archivos" >> documentos/notas.txt
cat documentos/notas.txt
```

**Paso 3: Copiar `notas.txt` a `scripts` como `backup_notas.txt` y moverlo a `imagenes`**
```bash
cp documentos/notas.txt scripts/backup_notas.txt
ls scripts
mv scripts/backup_notas.txt imagenes/
ls imagenes
```

**Paso 4: Crear `resumen.txt`, redireccionar y añadir contenido**
```bash
touch documentos/resumen.txt
cat documentos/notas.txt > documentos/resumen.txt
echo "Línea agregada sin sobrescribir usando >>" >> documentos/resumen.txt
cat documentos/resumen.txt
```

**Paso 5: Eliminar `backup_notas.txt` y la carpeta `imagenes`**
```bash
rm imagenes/backup_notas.txt
rmdir imagenes
ls
```

**Paso 6: Volcar el historial con una tubería**
```bash
history 1 | cat > tarea-s1-juan_bravo.txt
cat tarea-s1-juan_bravo.txt
```

**Paso 7: Subir el proyecto a GitHub**
```bash
git init
git add .
git commit -m "Tarea semana 1: comandos de Linux"
git branch -M main
git remote add origin https://Jbra420@github.com/Jbra420/tarea-s1-comandos-linux.git
git push -u origin main --force
```

## 9. Resultados esperados
Al finalizar la práctica, el directorio `proyecto_comandos` contiene las carpetas `documentos` y `scripts` (la carpeta `imagenes` fue eliminada al quedar vacía). En `documentos` se encuentran `notas.txt`, con tres líneas de texto, y `resumen.txt`, que contiene una copia del contenido de `notas.txt` más una línea adicional añadida con `>>`. Además, el archivo `tarea-s1-juan_bravo.txt` registra el historial de los comandos ejecutados, generado mediante una tubería. Todo el proyecto, junto con este informe, se encuentra publicado en un repositorio público de GitHub.

## 10. Bibliografía
- Shotts, W. (2019). *The Linux command line: A complete introduction* (2.ª ed.). No Starch Press.
- Free Software Foundation. (s.f.). *GNU Bash manual*. https://www.gnu.org/software/bash/manual/
- GitHub. (s.f.). *GitHub Docs: Getting started with Git*. https://docs.github.com/es/get-started
