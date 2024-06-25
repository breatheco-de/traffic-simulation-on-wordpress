# Simulación de trafico al sitio wordpress

<!-- hide -->

> By [@rosinni](https://github.com/rosinni) and [other contributors](https://github.com/4GeeksAcademy/deploying-wordpress-debian/graphs/contributors) at [4Geeks Academy](https://4geeksacademy.co/)

![last commit](https://img.shields.io/github/last-commit/4geeksacademy/installing-kali-linux-on-virtual-machine)
[![build by developers](https://img.shields.io/badge/build_by-Developers-blue)](https://4geeks.com)
[![build by developers](https://img.shields.io/twitter/follow/4geeksacademy?style=social&logo=twitter)](https://twitter.com/4geeksacademy)

*These instructions are [available in english](https://github.com/4GeeksAcademy/deploying-wordpress-debian/blob/main/README.md)*
<!-- endhide -->


<!-- hide -->

### Antes de empezar...

> ¡Te necesitamos! Estos ejercicios se crean y mantienen en colaboración con personas como tú. Si encuentras algún error o falta de ortografía, contribuye y/o repórtalo.

<!-- endhide -->

## 🌱 ¿Cómo empezar este proyecto?

### Instalación local:

Clona el repositorio en tu ambiente local [repositorio](https://github.com/breatheco-de/traffic-simulation-on-wordpress).

<!-- 1. Instala LearnPack, el package manager para tutoriales de aprendizaje y el HTML compiler plugin para LearnPack, asegúrate también de tener node.js 14+:

```bash
$ npm i learnpack -g
$ learnpack plugins:install learnpack-html
```

2. Descarga estos ejercicios en particular usando LearnPack y luego `cd` para entrar en la carpeta:

```bash
$ learnpack download html-forms-tutorial-exercises
$ cd html-forms-tutorial-exercises
```

> Nota: Una vez que termines de descargar, encontrarás una carpeta "exercises" que contiene todos los ejercicios.

3. Inicializa el tutorial/ejercicios ejecutando el siguiente comando en el mismo nivel donde se encuentra tu archivo learn.json:

```bash
$ npm i jest@24.8.0 -g
$ learnpack start
```

hide -->

## 📝 Instrucciones

En ésta práctica aprenderás como generar tráfico artificial en el sitio Wordpress e implementarás herramientas de monitoreo para detectar las oleadas de peticiones y evaluar el desempeño del servidor.

IMPORTANTE: Para llevar a cabo este proyecto vamos a necesitar 2 maquinas virtuales. Una de ellas será la maquina virtual de debian donde construimos el sitio web de wordpress anteriormente.

### ¿Qué computadoras vamos a utilizar?


* Máquina virtual con Kali Linux (Atacante): Para generar el tráfico.
* Máquina virtual con Debian (Servidor Web): Donde tenemos alojado el servidor Apache y el sitio WordPress.

### Paso 1: Configurar la Red en VirtualBox

#### Configurar la Red de la Máquina Debian (Servidor Web):
* Abre VirtualBox.
* Selecciona tu máquina virtual con Debian y haz clic en "Configuración".
* Ve a la sección "Red".
* Asegúrate de que el "Adaptador 1" esté habilitado y configurado como "Adaptador puente".
* Selecciona el adaptador de red física de tu host que deseas usar para la conexión (puede ser Wi-Fi o Ethernet).
* Guarda los cambios y cierra la ventana de configuración.


#### Configurar la Red de la Máquina Kali Linux (Atacante):
* Selecciona tu máquina virtual con Kali Linux y haz clic en "Configuración".
* Ve a la sección "Red".
* Asegúrate de que el "Adaptador 1" esté habilitado y configurado como "Adaptador puente".
* Selecciona el mismo adaptador de red física de tu host que seleccionaste para la máquina Debian.
* Guarda los cambios y cierra la ventana de configuración.
# COLOCAR IMAGEN

### Paso 2: Obtener la Dirección IP de las Máquinas para poderlas conectar entre sí.

Con "Adaptador puente" configurado, las máquinas deberían obtener una dirección IP automáticamente de tu router o servidor DHCP de la red.

#### En la Máquina Debian (Servidor Web):
* Inicia la máquina virtual Debian.
* Abre una terminal y ejecuta el siguiente comando para ver la dirección IP asignada:
```bash
$ ip addr show
```
> Busca la sección correspondiente a tu interfaz de red (usualmente eth0 o enp0s3) y encuentra la línea que dice inet. Ahí verás la dirección IP asignada, algo como 192.168.1.x.

#### En la Máquina Kali Linux (Atacante):
* Inicia la máquina virtual Kali Linux.
* Abre una terminal y ejecuta el siguiente comando para ver la dirección IP asignada:

```bash
$ ip addr show
```

> Busca la sección correspondiente a tu interfaz de red (usualmente eth0 o enp0s3) y encuentra la línea que dice inet. Ahí verás la dirección IP asignada, algo como 192.168.1.x.

### PASO 3: Verificar la Conexión Entre las Máquinas

#### Desde la Máquina Kali Linux (Atacante):
* Abre una terminal y haz ping a la máquina Debian para verificar la conexión:

```bash
$ ping <IP_debian>
```

> Reemplaza <IP_debian> con la dirección IP que obtuviste para la máquina Debian.

#### Desde la Máquina Debian (Servidor Web):
* Abre una terminal y haz ping a la máquina Kali Linux para verificar la conexión:

```bash
$ ping <IP_kali>
```

> Reemplaza <IP_kali> con la dirección IP que obtuviste para la máquina Kali.

# ANEXAR IMAGEN DE COMO SE VA VER SI ESTÁN CONECTADAS


### PASO 4: Simular Tráfico en el Sitio Web

#### En la Máquina Kali Linux (Atacante):
Usaremos como herramienta ab (Apache Benchmark) para generar tráfico en el sitio web. 

COLOCA ACA LAS INSTRUCCIONES DE APACHE BENCHMARK







## Colaboradores

Gracias a estas personas maravillosas ([emoji key](https://github.com/kentcdodds/all-contributors#emoji-key)):

1. [Rosinni Rodríguez (rosinni)](https://github.com/rosinni) contribución: (build-tutorial) ✅, (documentación) 📖
  
2. [Alejandro Sanchez (alesanchezr)](https://github.com/alesanchezr),  contribución: (detector bugs) 🐛

3. [Lorena Gubaira (lorenagubaira)](https://github.com/lorenagubaira), contribution: (detector bugs) 🐛, contribution: (editor), (tranducción) 🌎

Este proyecto sigue la especificación [all-contributors](https://github.com/kentcdodds/all-contributors). ¡Todas las contribuciones son bienvenidas!

Este y otros ejercicios son usados para [aprender a programar](https://4geeksacademy.com/es/aprender-a-programar/aprender-a-programar-desde-cero) por parte de los alumnos de 4Geeks Academy [Coding Bootcamp](https://4geeksacademy.com/us/coding-bootcamp) realizado por [Alejandro Sánchez](https://twitter.com/alesanchezr) y muchos otros contribuyentes. Conoce más sobre nuestros [Cursos de Programación](https://4geeksacademy.com/es/curso-de-programacion-desde-cero?lang=es) para convertirte en [Full Stack Developer](https://4geeksacademy.com/es/coding-bootcamps/desarrollador-full-stack/?lang=es), o nuestro [Data Science Bootcamp](https://4geeksacademy.com/es/coding-bootcamps/curso-datascience-machine-learning).Tambien puedes adentrarte al mundo de ciberseguridad con nuestro [Bootcamp de ciberseguridad](https://4geeksacademy.com/es/coding-bootcamps/curso-ciberseguridad).
<!-- endhide -->
