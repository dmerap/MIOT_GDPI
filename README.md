![Banner](img/MIOT_GDPI_header.png)
# MIOT_GDPI
Repositorio para las prácticas de la materia Gemelos Digitales para Plantas Industriales asociada al Máster Universitario en Internet de las Cosas - IoT (MUIoT).


# Profesorado
* David Mera Pérez (USC, coordinador)
* Julio Garrido Campos (UVigo)
* Francisco Zayas Gato (UDC)

# Entorno de desarrollo
Las prácticas de esta materia se desarrollarán a través de Notebooks. Para ejecutarlas, necesitarás instalar Python, un servidor de Notebooks (por ejemplo, Jupyter) y todos los paquetes requeridos para cada una de las unidades prácticas. Hay diferentes opciones para poder desarrollar los trabajos (podéis emplear la que consideréis más apropiada). En este manual os damos varias alternativas:
1. [Google Colab](https://colab.research.google.com/): Colab es un entorno de desarrollo de Google que permite cargar y crear Notebooks. También permite gestionar entornos e instalar nuevos paquetes (librerías) ejecutando el comando  <code>!pip install nombre_paquete</code>. Podéis acceder directamente con vuestra cuenta de Google, aunque la cuenta gratuita tiene algunas limitaciones (la mayoría relacionadas con el acceso a recursos informáticos). 


2. [Python](https://www.python.org/downloads/) y [pip](https://pip.pypa.io/en/stable/installation/): Instalación directa de Python y pip a nivel de sistema (pip se instala automáticamente si has instalado Python desde la página web oficial). Una vez instalado Python, es necesario instalar Jupyter y el resto de los paquetes para el desarrollo de las prácticas. La instalación de paquetes se hace a nivel de sistema empleando el comando <code>pip install nombre_paquete</code>. Esta aproximación es simple, pero instalar a nivel de sistema puede generar conflictos.
3. [Anaconda](https://www.anaconda.com/) es un framework de desarrollo basado en entornos virtuales y enfocado a la Ciencia de Datos y el Machine Learning, que está disponible en Windows, Linux y MacOS. Este framework está compuesto por diferentes paquetes y software, incluyendo Jupyter y [conda](https://docs.conda.io/en/latest/). Conda es un sistema para la gestión de entornos virtuales que nos permite tener diferentes entornos conviviendo en el mismo sistema. Cada entorno puede instalar los paquetes y versiones necesarios independientemente del resto. Mientras que `pip` instala paquetes a nivel de sistema y puede causar conflictos, `conda` permite tener cada configuración  en un entorno virtual separado sin conflictos.  Todas las dependencias son gestionadas por conda. Los usuarios pueden activar y desactivar entornos virtuales a su discreción. La forma de gestionar los paquetes es usando el comando <code>conda install xxx</code> en lugar de `pip`. En caso de que un paquete no esté disponible en `conda`, es posible instalarlo a través de una versión de `pip` interna asociada al sistema `conda`.
4. [Miniconda](https://docs.conda.io/en/latest/miniconda.html) es un instalador mínimo gratuito para conda,  que está disponible en Windows, Linux y MacOS. Es una versión pequeña de Anaconda que incluye *solo* conda, Python, los paquetes de los que dependen y un pequeño número de otros paquetes útiles.
Anaconda es un framework enorme con muchos paquetes innecesarios para nuestras prácticas. Miniconda permite al usuario instalar solo los paquetes mínimos y necesarios. Cabe destacar que Jupyter no está incluido en Miniconda y que debe instalarse como un nuevo paquete  <code>conda install jupyter</code>.

## Entornos virtuales
**Documentación oficial: comandos de conda para la gestión de entornos virtuales**

[https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html](
https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)

**Conda cheatsheet**

[https://docs.conda.io/projects/conda/en/latest/_downloads/843d9e0198f2a193a3484886fa28163c/conda-cheatsheet.pdf](
https://docs.conda.io/projects/conda/en/latest/_downloads/843d9e0198f2a193a3484886fa28163c/conda-cheatsheet.pdf)



### Comandos útiles de conda
**Creación de un entorno**
<code> conda create --name environment_name</code>

Es posible indicar la versión específica de Python que contendrá el entorno virtual.

<code> conda create --name environment_name python=x.y.z</code>

**Activación del entorno**
<code>conda activate  environment_name</code>

La activación del entorno nos permite trabajar con los paquetes y características de ese entorno. Es importante tener en cuenta que fuera del entorno estas librerías no tienen por que existir (a nivel de sistema).

**Desactivación del entorno**
<code>conda deactivate</code>

Este comando nos permite salir del entorno virtual activado. Fijaos que en este caso no es necesario indicar el nombre.

**Eliminar un entorno virtual**
<code>conda remove  --name environment_name -all</code>

**Importante:** Esta operación no puede deshacerse.

**Lista todos los entornos virtuales presentes en el sistema**
<code>conda info --envs</code>

Comando alternativo

<code>conda envs list</code>

**Instalar un nuevo paquete en el entorno virtual**
<code>conda install package_name</code>

**Importante**: La instalación del paquete se producirá en el entorno virtual activo.

**Listar los paquetes instalados en un entorno virtual**
<code>conda list</code>

Se mostrarán los paquetes instalados en el entorno virtual activo.

**Exportar la configuración del entorno a un fichero**
<code>conda env export > environment_file_name.yml</code>

Muy útil para reproducir el entorno de ejecución. **Importante**: Es dependiente de la plataforma.

**Exportar la configuración del entorno a un fichero (multiplataforma)**
<code>conda env export --from-history > environment_file_name.yml</code>

Muy útil para reproducir el entorno de ejecución. **Importante**:Permite exportar e importar entre diferentes plataformas (ej. Desde Linux a Windows).

**Crear e importar la configuración de un entorno desde un fichero**
<code>conda env create -f environment_file_name.yml</code>

## Creación del entorno virtual para las prácticas
<code>conda create --name miot_ml</code>



**Paquetes requeridos para las prácticas**

Para instalar los paquetes requeridos para las prácticas es necesario ejecutar el siguiente comando (sustituid los *nombre_paquete* por los paquetes concretos): 

<code>conda install nombre_paquete1 nombre_paquete2 ... nombre_paquete_n</code>

Los paquetes requeridos para las prácticas son: