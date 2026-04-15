![Banner](img/MIOT_GDPI_header.png)
# MIOT_GDPI

Este repositorio contiene un conjunto de tutoriales que sirven de introducción a los temas tratados en la asignatura de Gemelos Digitales para Plantas Industriales (GDPI) asociada al Máster Universitario en Internet de las Cosas - IoT (MUIoT) impartido por las tres universidades de Galicia: Universidad de A Coruña (UDC), Universidad de Santiago de Compostela (USC) y Universidad de Vigo (UVigo).

- [Equipo docente](#equipo-docente)
- [Entorno de desarrollo](#entornos-de-desarrollo)
 - [Gestión de paquetes y entornos con uv](#gesti%C3%B3n-de-paquetes-y-entornos-con-uv)
 - [Gestión de paquetes y entornos con CONDA](#gesti%C3%B3n-de-paquetes-y-entornos-con-conda) 



# Equipo docente
## Teoría
* David Mera Pérez (USC, coordinador)
## Prácticas
* David Mera Pérez (USC)
* Alejandro Budiño Regueira (USC)
* Julio Garrido Campos (UVigo)
* Francisco Zayas Gato (UDC)

# Entornos de desarrollo
Las prácticas de esta materia se desarrollarán a través de Notebooks. Para ejecutarlas, necesitarás instalar Python, un servidor de Notebooks (por ejemplo, Jupyter) y todos los paquetes requeridos para cada una de las unidades prácticas. Hay diferentes opciones para poder desarrollar los trabajos (podéis emplear la que consideréis más apropiada). En este manual os damos varias alternativas:


1. [Google Colab](https://colab.research.google.com/): Colab es un entorno de desarrollo de Google que permite cargar y crear Notebooks. También permite gestionar entornos e instalar nuevos paquetes (librerías) ejecutando el comando  <code>!pip install nombre_paquete</code>. Podéis acceder directamente con vuestra cuenta de Google, aunque la cuenta gratuita tiene algunas limitaciones (la mayoría relacionadas con el acceso a recursos informáticos). 

2. [Python](https://www.python.org/downloads/) y [pip](https://pip.pypa.io/en/stable/installation/): Instalación directa de Python y pip a nivel de sistema (pip se instala automáticamente si has instalado Python desde la página web oficial). Una vez instalado Python, es necesario instalar Jupyter y el resto de los paquetes para el desarrollo de las prácticas. La instalación de paquetes se hace a nivel de sistema empleando el comando <code>pip install nombre_paquete</code>. Esta aproximación es simple, pero instalar a nivel de sistema puede generar conflictos.
3. [Anaconda](https://www.anaconda.com/) es un framework de desarrollo basado en entornos virtuales y enfocado a la Ciencia de Datos y el Machine Learning, que está disponible en Windows, Linux y MacOS. Este framework está compuesto por diferentes paquetes y software, incluyendo Jupyter y [conda](https://docs.conda.io/en/latest/). Conda es un sistema para la gestión de entornos virtuales que nos permite tener diferentes entornos conviviendo en el mismo sistema. Cada entorno puede instalar los paquetes y versiones necesarios independientemente del resto. Mientras que `pip` instala paquetes a nivel de sistema y puede causar conflictos, `conda` permite tener cada configuración  en un entorno virtual separado sin conflictos.  Todas las dependencias son gestionadas por conda. Los usuarios pueden activar y desactivar entornos virtuales a su discreción. La forma de gestionar los paquetes es usando el comando <code>conda install xxx</code> en lugar de `pip`. En caso de que un paquete no esté disponible en `conda`, es posible instalarlo a través de una versión de `pip` interna asociada al sistema `conda`.
4. [Miniconda](https://docs.conda.io/en/latest/miniconda.html) es un instalador mínimo gratuito para conda,  que está disponible en Windows, Linux y MacOS. Es una versión pequeña de Anaconda que incluye *solo* conda, Python, los paquetes de los que dependen y un pequeño número de otros paquetes útiles.
Anaconda es un framework enorme con muchos paquetes innecesarios para nuestras prácticas. Miniconda permite al usuario instalar solo los paquetes mínimos y necesarios. Cabe destacar que Jupyter no está incluido en Miniconda y que debe instalarse como un nuevo paquete  <code>conda install jupyter</code>.

5. [UV](https://docs.astral.sh/uv/) (*Recomendado*) Gestor de paquetes y entornos de Python caracterizado por su rapidez y que sustituye "oficialmente" a conda en este curso. Crea entornos virtuales estándar y utiliza flujos de trabajo compatibles con pip. La documentación oficial está disponible en este enlace.

## Gestión de paquetes y entornos con uv
Aunque los estudiantes pueden elegir el método más conveniente para ellos, oficialmente este curso empleará `uv` como gestor de entornos y dependencias de Python. A continuación se describe brevemente **como gestionar los entornos a través de esta herramienta suponiendo que el S.O. es Linux**.

### Instalación de UV
Existen [diferentes](https://docs.astral.sh/uv/getting-started/installation/) alternativas para instalar `uv`, incluyendo a través de pip, no obstante, `uv`proporciona un instalador independiente que descarga e instala la app en vuestro.

<code>
curl -LsSf https://astral.sh/uv/install.sh | sh
</code>

### Creación del entorno virtual
Suponiendo que hemos descargado el repositorio remoto a nuestra máquina, accederemos a la carpeta (MIOT_GDPI) del repositorio desde una terminal y ejecutaremos:

<code>
uv venv --python 3.12
</code>

Esto creará una carpeta oculta con el entorno virtual en `.venv`. Para este proyecto emplearemos la version 3.12 de Python.

### Activación del entorno
Los entornos creados no están activados por defecto, es necesario activarlos para que las instalaciones de las dependencias se realicen en dicho entorno y no a nivel general del sistema.
`uv`no proporciona un comando de activación propio, es necesario emplear el script estándar de Python presente en la carpeta `.venv`.

<code>
source .venv/bin/activate
</code>

### Desactivar el entorno completamente
Es suficiente con ejecutar el comando `deactivate`

### Borrar un entorno
Es suficiente con eliminar la carpeta oculta creada:

<code>
rm -rf .venv
</code>

### Instalar todas las dependencias del proyecto
**Con el entorno correspondiente activado**, todas las dependencias están definidas en `requirements.txt` y estas se pueden instalar con: 

<code>
pip install -r requirements.txt
</code>

Como el entorno se creó con `uv`, el comando `pip` instala los paquetes dentro del entorno virtual activado.

### Instalar un solo paquete dentro del entorno virtual 
Si necesitamos instalar un determinado paquete aislado, lo haremos directamente con `pip`:

<code>
pip install nombre_del_paquete
</code>

Ejemplo: 

<code>
pip install river
</code>

### Ejecutar comandos dentro del entorno
Si el entorno está activado, la ejecución de un comando en una terminal es la habitual  pero, si queremos ejecutar un comando sin activar el entorno o tenemos algún conflicto (tenemos entornos virtuales de CONDA y de `uv` al mismo tiempo), la forma de forzar a que el comando se ejecute en el marco del entorno virtual `uv` es:

<code>
uv run comando
</code>

Ejemplo:
<code>
uv run jupyter notebook
</code>
Esto garantiza que el comando se ejecute utilizando el entorno virtual del proyecto.

### Resumen de comandos de `uv`


| tarea | Comando recomendado |
|---|---|
| Crear entorno | `uv venv` |
| Activar entorno | `source .venv/bin/activate` |
| Instalar dependencias (entorno activado) | `pip install -r requirements.txt` |
| Instalar un solo paquete (entorno activado)| `pip install package_name` |
| Instalar un paquete sin activación | `uv pip install package_name` |
| Ejecutar un comando sin activación | `uv run command` |





## Gestión de paquetes y entornos con CONDA
Se proporciona esta guía a modo *legacy* y para los estudiantes que prefieren gestionar el entorno virtual con CONDA, aunque el soporte desde la parte docente será limitado.


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

### Creación del entorno virtual para las prácticas con CONDA
<code>conda create --name miot_gdpi</code>

**Nota**: Apuntad el directorio de instalación para poder emplear *pip* dentro del entorno virtual.


A continuación, activad el entorno recién creado: 

<code>conda activate miot_gdpi</code>

**Paquetes requeridos para las prácticas aprendizaje incremental (*Online Learning*)**

<code>conda install jupyter scikit-learn=1.7.2 pandas matplotlib python-graphviz rich</code>

**Nota**: Necesitamos la versión 1.7.2 de scikit-learn por problemas de compatibilidad con la versión 0.23 de River.

Para obtener la versión más reciente del paquete River, deberás instalarlo usando `pip` dentro de tu entorno virtual. **Asegúrate de utilizar la versión de pip que se encuentra específicamente dentro de tu entorno virtual, y no la global**. Localiza el directorio de tu entorno virtual, que normalmente se encuentra en una ruta similar a /anaconda/envs/nombre_del_entorno_virtual/ y ejecuta el siguiente comando.

<code>/home/user/anaconda/envs/miot_gdpi/bin/pip install river==0.23</code>

**Nota**: En la actualidad River está en la versión 0.24 pero, por estabilidad, trabajaremos con la versión 0.23.


**Paquetes requeridos para las prácticas con modelos de redes neuronales profundas**

<code>conda install seaborn kagglehub </code>

Para obtener las versiones más recientes de **Keras** y **Tensorflow** emplearemos el comando `pip` dentro de nuestro entorno virtual.**Asegúrate de utilizar la versión de pip que se encuentra específicamente dentro de tu entorno virtual, y no la global**. Localiza el directorio de tu entorno virtual, que normalmente se encuentra en una ruta similar a /anaconda/envs/nombre_del_entorno_virtual/ y ejecuta el siguiente comando.

<code>/home/user/anaconda/envs/miot_gdpi/bin/pip install keras tensorflow</code>







**Nota**: Para localizar la ruta del entorno virtual podéis ejecutar el siguiente comando (Linux):

<code>echo $CONDA_PREFIX</code>

**IMPORTANTE**: Todos los comandos de esta sección están pensados para ejecutarse dentro del entorno, por lo que es necesario tenerlo activado.





