# Traffic simulation on the wordpress site

This project seeks to generate artificial traffic from a Kali Linux machine to a website hosted on a Debian server using the Apache Benchmark (ab) tool. Additionally, monitoring tools will be implemented on the server to detect traffic surges and evaluate its performance.

<!-- hide -->
<a href="https://www.4geeksacademy.co"><img height="280" align="right" src="https://github.com/4GeeksAcademy/deploying-wordpress-debian/blob/master/js-bg-badge.png"></a>


> By [@rosinni](https://github.com/rosinni) and [other contributors](https://github.com/4GeeksAcademy/deploying-wordpress-debian/graphs/contributors) at [4Geeks Academy](https://4geeksacademy.co/)

![last commit](https://img.shields.io/github/last-commit/4geeksacademy/installing-kali-linux-on-virtual-machine)
[![build by developers](https://img.shields.io/badge/build_by-Developers-blue)](https://4geeks.com)
[![build by developers](https://img.shields.io/twitter/follow/4geeksacademy?style=social&logo=twitter)](https://twitter.com/4geeksacademy)

*These instructions are [available in english](https://github.com/4GeeksAcademy/deploying-wordpress-debian/blob/main/README.md)*
<!-- endhide -->

<!-- hide -->
### Before you start...

> We need you! These exercises are built and maintained in collaboration with contributors such as yourself. If you find any bugs or misspellings please contribute and/or report them.
<!-- endhide -->

<!-- hide -->


## 🌱 How to start a project?


### Local Installation:
Clone the repository to your local environment [repository](https://github.com/breatheco-de/traffic-simulation-on-wordpress) and follow the instructions in the README file.


### Requirements

To carry out this project, we will need 2 virtual machines. One will be the Debian virtual machine where we previously built the WordPress website, and the other will be the Kali virtual machine as the attacker.

* Oracle VirtualBox
* Virtual machine with Kali Linux (Attacker): To generate traffic.
* Virtual machine with Debian (Web Server): Where we have the Apache server and the WordPress site hosted.

## 📝 Instructions

### Step 1: Configure the Network in VirtualBox

#### Configure the Network of the Debian Machine (Web Server):
* Open VirtualBox.
* Select your Debian virtual machine and click on "Settings".
* Go to the "Network" section.
* Ensure that "Adapter 1" is enabled and set to "Bridged Adapter".
* En el campo "Nombre", selecciona el adaptador de red física que deseas usar (el que tu host está utilizando para conectarse a la red, como Wi-Fi o Ethernet). Esto suele ser algo como "Intel(R) Ethernet Connection" o "Wi-Fi".
* Save the changes and close the settings window.


#### Configure the Network of the Kali Linux Machine (Attacker):
* Select your Kali Linux virtual machine and click on "Settings".
* Go to the "Network" section.
* Ensure that "Adapter 1" is enabled and set to "Bridged Adapter".
* In the "Name" field, select the same physical network adapter you selected for the Debian machine.
* Save the changes and close the settings window.


![Configurar maquina virtual](assets/config-virtual-machine.png)



### Step 3: Verify the Connection Between the Machines

#### From the Kali Linux Machine (Attacker):
* Open a terminal and ping the Debian machine to verify the connection:

```bash
$ ping <IP_debian>
```

> Replace <IP_debian> with the IP address you obtained for the Debian machine.

#### From the Debian Machine (Web Server): 
* Open a terminal and ping the Kali Linux machine to verify the connection:

```bash
$ ping <IP_kali>
```
> Replace <IP_kali> with the IP address you obtained for the Kali machine.

Graphical example of how the pings look when connected:
![Graphical example of how the pings look when connected:](assets/ping-view.png)


### Step 4: Simulate Traffic on the Website

#### On the Kali Linux Machine (Attacker):
We will use Apache Benchmark (ab) as a tool to generate traffic on the website.

#### Installation and Usage of Apache Benchmark
Apache Benchmark (ab) is a tool that allows you to generate test traffic to a web server. Follow these steps to install and use ab from Kali Linux:
1. Installation of Apache Benchmark

```bash
$ sudo apt-get update
$ sudo apt-get install apache2-utils
```

2. Generate Traffic to the Website

```bash
$ ab -n 1000 -c 10 http://<IP_debian>/
```
***The command  `ab -n 1000 -c 10 http://<IP_debian>/` hwill make Apache Bench send 1000 HTTP requests to the web server at http://<IP_debian>/, with 10 requests being made concurrently, simulating 10 concurrent users accessing the server..***

> NOTE: Replace <IP_debian> with the IP address of the Debian server.


### Step 5: Monitoring Server Performance
On the Debian server, we are going to install monitoring tools like htop to observe the performance during the tests.

#### Installing htop
```bash
$ sudo apt-get update
$ sudo apt-get install htop
```

#### Real-Time Monitoring with htop

`htop` is an interactive process monitoring tool that provides a detailed view of the system resource usage. Run the following command in the terminal to monitor CPU, memory, and other system resources in real-time while running tests with Apache Benchmark.

```bash
$ htop
```
You will see something like this:
![monitoreo con htop](assets/monitor-htop.png)


* **CPU Usage**: Shows real-time CPU usage, usually divided into bars representing each CPU core.
* **Memory Usage**: Displays RAM and swap memory usage.
* **Tasks**: Lists active processes with details such as PID, user, CPU and memory usage, runtime, and the command that started the process.
* **Load Average**: Shows the system load average over the last 1, 5, and 15 minutes.
* **Uptime**: Indicates how long the system has been running since the last reboot.

## Project Delivery

In the cloned repository, you must submit 2 reports.

* The first report should be named `report_ab.txt`. Generate this report when performing the attack on your Kali virtual machine with the following command:

```bash
$ ab -n 5000 -c 200 http://<IP_debian>/ > report_ab.txt
```

* The second report should be created with the name `report_htop.txt` and include observations on the server performance on your Debian machine while using htop.

> ***Copy these lines into the `report_htop.txt` file and fill in the corresponding information.***
```yml
  observations:
  evaluation_if_server_could_handle_load:
    - performance_metrics:
        - stable_memory: # Here you can note how many requests per second maintained stable memory usage
        - cpu_load_average: # Here you can note what average CPU load percentage was maintained

  specification_of_excessive_resource_usage:
    - cpu_peak_usage:
        - observed: true  # Indicate if a CPU usage peak of 90% was observed during the first few minutes of maximum load (the value would be true or false)
        - peak_percentage: 90
        - request_count_at_peak:
            - value:  # Here you can note the specific number of requests at which the peak occurred
```






<!-- hide -->
## Contributors

Thanks goes to these wonderful people ([emoji key](https://github.com/kentcdodds/all-contributors#emoji-key)):

1. [Rosinni Rodríguez (rosinni)](https://github.com/rosinni) contribution: (build-tutorial) ✅, (documentation) 📖
  
2. [Alejandro Sanchez (alesanchezr)](https://github.com/alesanchezr),  contribution: (bug reports) 🐛

3. [Lorena Gubaira (lorenagubaira)](https://github.com/lorenagubaira), contribution: (bug reports) 🐛, contribution: (editor), (translation) 🌎

This project follows the [all-contributors](https://github.com/kentcdodds/all-contributors) specification. Contributions of any kind are welcome!

This and many other exercises are built by students as part of the 4Geeks Academy [Coding Bootcamp](https://4geeksacademy.com/us/coding-bootcamp) by [Alejandro Sánchez](https://twitter.com/alesanchezr) and many other contributors. Find out more about our [Full Stack Developer Course](https://4geeksacademy.com/us/coding-bootcamps/part-time-full-stack-developer), and  [Data Science Bootcamp](https://4geeksacademy.com/us/coding-bootcamps/datascience-machine-learning).You can alse deepdive in the world of cybersecurity with our [Cybersecurity Bootcamp](https://4geeksacademy.com/us/coding-bootcamps/cybersecurity)
<!-- endhide -->