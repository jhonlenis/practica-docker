# practica-docker

# Lab-Docker extrae una imagen del repositorio.


El comando docker search alpine es la herramienta que utilizas para explorar el catálogo de Docker Hub sin salir de tu terminal. Es el equivalente a usar la barra de búsqueda en el sitio web oficial de Docker.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $  docker search alpine
NAME                DESCRIPTION                                     STARS     OFFICIAL
alpine              A minimal Docker image based on Alpine Linux…   11477     [OK]
alpine/git          A  simple git container running in alpine li…   252       
alpine/socat        Run socat command in alpine container           115       
alpine/curl                                                         12        
alpine/helm         Auto-trigger docker build for kubernetes hel…   70        
alpine/k8s          Kubernetes toolbox for EKS (kubectl, helm, i…   65        
alpine/bombardier   Auto-trigger docker build for bombardier whe…   28        
alpine/httpie       Auto-trigger docker build for `httpie` when …   22        
alpine/terragrunt   Auto-trigger docker build for terragrunt whe…   18        
alpine/openssl      openssl                                         8         
alpine/kubectl      Kubernetes command-line tool for managing cl…   1         
alpine/flake8       Auto-trigger docker build for fake8 via ci c…   2         
alpine/psql         psql — The PostgreSQL Command-Line Client       4         
alpine/ansible      run ansible and ansible-playbook in docker      36        
alpine/jmeter       run jmeter in Docker                            9         
alpine/semver       Docker tool for semantic versioning             4         
alpine/java         Repo containing the build scripts to produce…   5         
alpine/xml          several xml tools to work on xml file as jq …   2         
alpine/openclaw     OpenClaw - Your own personal AI assistant. A…   74        
alpine/mongosh      mongosh - MongoDB Command Line Database Tools   2         
alpine/mysql        mysql client                                    7         
alpine/cfn-nag      Auto-trigger docker build for cfn-nag when n…   0         
alpine/gcloud       Auto-trigger docker build for gcloud (google…   0         
alpine/crane                                                        0         
alpine/bundle       This repository has been archived by the own…   1 

Este comando es el punto de partida para trabajar con contenedores. Lo que acabas de hacer es descargar la "plantilla" o "molde" de Alpine Linux desde la nube (Docker Hub) a tu computadora local.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker pull alpine
Using default tag: latest
latest: Pulling from library/alpine
589002ba0eae: Pull complete 
Digest: sha256:25109184c71bdad752c8312a8623239686a9a2071e8825f20acb8f2198c3f659
Status: Downloaded newer image for alpine:latest
docker.io/library/alpine:latest

(/ #) no es tu computadora ni tu Codespace, es el interior del contenedor Alpine
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker run -it --name alpine_container alpine /bin/sh
/ # ls -a
.           dev         media       root        sys
..          etc         mnt         run         tmp
.dockerenv  home        opt         sbin        usr
bin         lib         proc        srv         var

# Lab-Docker Run a Container


El comando sudo apt update es el que utilizas para actualizar la lista de precios y productos (paquetes) de los almacenes de software (repositorios) en Linux. No instala nada nuevo, solo revisa qué versiones hay disponibles para que tu sistema sepa qué puede descargar.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo apt update
Hit:1 https://packages.microsoft.com/repos/microsoft-ubuntu-noble-prod noble InRelease
Get:2 https://dl.yarnpkg.com/debian stable InRelease        
Hit:3 https://repo.anaconda.com/pkgs/misc/debrepo/conda stable InRelease
Hit:4 http://security.ubuntu.com/ubuntu noble-security InRelease
Err:2 https://dl.yarnpkg.com/debian stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 62D54FD4003F6525
Hit:5 http://archive.ubuntu.com/ubuntu noble InRelease
Hit:6 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:7 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Reading package lists... Done
W: GPG error: https://dl.yarnpkg.com/debian stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 62D54FD4003F6525
E: The repository 'https://dl.yarnpkg.com/debian stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


El comando sudo apt install docker.io es el que utilizas para instalar el motor de Docker directamente desde los repositorios oficiales de Ubuntu.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo apt install docker.io
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following package was automatically installed and is no longer required:
  moby-tini
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  apparmor bridge-utils containerd dns-root-data
  dnsmasq-base libapparmor1 libnftables1 moby-compose
  netcat-openbsd nftables ubuntu-fan
Suggested packages:
  apparmor-profiles-extra apparmor-utils ifupdown
  aufs-tools btrfs-progs cgroupfs-mount | cgroup-lite
  debootstrap docker-buildx docker-compose-v2 docker-doc
  rinse zfs-fuse | zfsutils firewalld
Recommended packages:
  moby-cli
The following packages will be REMOVED:
  moby-cli moby-containerd moby-engine
The following NEW packages will be installed:
  apparmor bridge-utils containerd dns-root-data
  dnsmasq-base docker.io libnftables1 netcat-openbsd
  nftables ubuntu-fan
The following packages will be upgraded:
  libapparmor1 moby-compose
2 upgraded, 10 newly installed, 3 to remove and 133 not upgraded.
Need to get 76.8 MB of archives.
After this operation, 107 MB disk space will be freed.
Do you want to continue? [Y/n] y  
Get:1 https://packages.microsoft.com/repos/microsoft-ubuntu-noble-prod noble/main amd64 moby-compose amd64 5.1.0-ubuntu24.04u1 [8440 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libapparmor1 amd64 4.0.1really4.0.1-0ubuntu0.24.04.5 [50.5 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble/main amd64 netcat-openbsd amd64 1.226-1ubuntu2 [44.3 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 apparmor amd64 4.0.1really4.0.1-0ubuntu0.24.04.5 [638 kB]
Get:5 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libnftables1 amd64 1.0.9-1ubuntu0.1 [359 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 nftables amd64 1.0.9-1ubuntu0.1 [69.8 kB]
Get:7 http://archive.ubuntu.com/ubuntu noble/main amd64 bridge-utils amd64 1.7.1-1ubuntu2 [33.9 kB]
Get:8 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 containerd amd64 1.7.28-0ubuntu1~24.04.2 [38.4 MB]
Get:9 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 dns-root-data all 2024071801~ubuntu0.24.04.1 [5918 B]
Get:10 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 dnsmasq-base amd64 2.90-2ubuntu0.1 [376 kB]
Get:11 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 docker.io amd64 28.2.2-0ubuntu1~24.04.1 [28.3 MB]
Get:12 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 ubuntu-fan all 0.12.16+24.04.1 [34.2 kB]
Fetched 76.8 MB in 1s (101 MB/s) 
Preconfiguring packages ...
(Reading database ... 58629 files and directories currently installed.)
Preparing to unpack .../moby-compose_5.1.0-ubuntu24.04u1_amd64.deb ...
Unpacking moby-compose (5.1.0-ubuntu24.04u1) over (2.40.3-ubuntu24.04u1) ...
(Reading database ... 58627 files and directories currently installed.)
Removing moby-cli (28.5.1-ubuntu24.04u1) ...
Removing moby-engine (28.5.1-ubuntu24.04u1) ...
/usr/sbin/policy-rc.d returned 101, not running 'stop docker.service'
Unit /etc/systemd/system/docker.service is masked, ignoring.
The unit files have no installation config (WantedBy=, RequiredBy=, UpheldBy=,
Also=, or Alias= settings in the [Install] section, and DefaultInstance= for
template units). This means they are not meant to be enabled or disabled using systemctl.
 
Possible reasons for having these kinds of units are:
• A unit may be statically enabled by being symlinked from another unit's
  .wants/, .requires/, or .upholds/ directory.
• A unit's purpose may be to act as a helper for some other unit which has
  a requirement dependency on it.
• A unit may be started when needed via activation (socket, path, timer,
  D-Bus, udev, scripted systemctl call, ...).
• In case of template units, the unit is meant to be enabled with some
  instance name specified.
System has not been booted with systemd as init system (PID 1). Can't operate.
Failed to connect to bus: Host is down
Removing moby-containerd (1.7.29-ubuntu24.04u1) ...
/usr/sbin/policy-rc.d returned 101, not running 'stop containerd.service'
Unit /etc/systemd/system/containerd.service is masked, ignoring.
The unit files have no installation config (WantedBy=, RequiredBy=, UpheldBy=,
Also=, or Alias= settings in the [Install] section, and DefaultInstance= for
template units). This means they are not meant to be enabled or disabled using systemctl.
 
Possible reasons for having these kinds of units are:
• A unit may be statically enabled by being symlinked from another unit's
  .wants/, .requires/, or .upholds/ directory.
• A unit's purpose may be to act as a helper for some other unit which has
  a requirement dependency on it.
• A unit may be started when needed via activation (socket, path, timer,
  D-Bus, udev, scripted systemctl call, ...).
• In case of template units, the unit is meant to be enabled with some
  instance name specified.
System has not been booted with systemd as init system (PID 1). Can't operate.
Failed to connect to bus: Host is down
(Reading database ... 58590 files and directories currently installed.)
Preparing to unpack .../00-libapparmor1_4.0.1really4.0.1-0ubuntu0.24.04.5_amd64.deb ...
Unpacking libapparmor1:amd64 (4.0.1really4.0.1-0ubuntu0.24.04.5) over (4.0.1really4.0.1-0ubuntu0.24.04.4) ...
Selecting previously unselected package netcat-openbsd.
Preparing to unpack .../01-netcat-openbsd_1.226-1ubuntu2_amd64.deb ...
Unpacking netcat-openbsd (1.226-1ubuntu2) ...
Selecting previously unselected package apparmor.
Preparing to unpack .../02-apparmor_4.0.1really4.0.1-0ubuntu0.24.04.5_amd64.deb ...
Unpacking apparmor (4.0.1really4.0.1-0ubuntu0.24.04.5) ...
Selecting previously unselected package libnftables1:amd64.
Preparing to unpack .../03-libnftables1_1.0.9-1ubuntu0.1_amd64.deb ...
Unpacking libnftables1:amd64 (1.0.9-1ubuntu0.1) ...
Selecting previously unselected package nftables.
Preparing to unpack .../04-nftables_1.0.9-1ubuntu0.1_amd64.deb ...
Unpacking nftables (1.0.9-1ubuntu0.1) ...
Selecting previously unselected package bridge-utils.
Preparing to unpack .../05-bridge-utils_1.7.1-1ubuntu2_amd64.deb ...
Unpacking bridge-utils (1.7.1-1ubuntu2) ...
Selecting previously unselected package containerd.
Preparing to unpack .../06-containerd_1.7.28-0ubuntu1~24.04.2_amd64.deb ...
Unpacking containerd (1.7.28-0ubuntu1~24.04.2) ...
Selecting previously unselected package dns-root-data.
Preparing to unpack .../07-dns-root-data_2024071801~ubuntu0.24.04.1_all.deb ...
Unpacking dns-root-data (2024071801~ubuntu0.24.04.1) ...
Selecting previously unselected package dnsmasq-base.
Preparing to unpack .../08-dnsmasq-base_2.90-2ubuntu0.1_amd64.deb ...
Unpacking dnsmasq-base (2.90-2ubuntu0.1) ...
Selecting previously unselected package docker.io.
Preparing to unpack .../09-docker.io_28.2.2-0ubuntu1~24.04.1_amd64.deb ...
Unpacking docker.io (28.2.2-0ubuntu1~24.04.1) ...
Selecting previously unselected package ubuntu-fan.
Preparing to unpack .../10-ubuntu-fan_0.12.16+24.04.1_all.deb ...
Unpacking ubuntu-fan (0.12.16+24.04.1) ...
Setting up libapparmor1:amd64 (4.0.1really4.0.1-0ubuntu0.24.04.5) ...
Setting up libnftables1:amd64 (1.0.9-1ubuntu0.1) ...
Setting up nftables (1.0.9-1ubuntu0.1) ...
Setting up netcat-openbsd (1.226-1ubuntu2) ...
update-alternatives: using /bin/nc.openbsd to provide /bin/nc (nc) in auto mode
Setting up moby-compose (5.1.0-ubuntu24.04u1) ...
Setting up dnsmasq-base (2.90-2ubuntu0.1) ...
Setting up dns-root-data (2024071801~ubuntu0.24.04.1) ...
Setting up apparmor (4.0.1really4.0.1-0ubuntu0.24.04.5) ...
Created symlink /etc/systemd/system/sysinit.target.wants/apparmor.service → /usr/lib/systemd/system/apparmor.service.
Reloading AppArmor profiles 
Setting up bridge-utils (1.7.1-1ubuntu2) ...
Setting up containerd (1.7.28-0ubuntu1~24.04.2) ...
Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /usr/lib/systemd/system/containerd.service.
Setting up ubuntu-fan (0.12.16+24.04.1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/ubuntu-fan.service → /usr/lib/systemd/system/ubuntu-fan.service.
invoke-rc.d: could not determine current runlevel
invoke-rc.d: policy-rc.d denied execution of start.
Setting up docker.io (28.2.2-0ubuntu1~24.04.1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /usr/lib/systemd/system/docker.service.
Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /usr/lib/systemd/system/docker.socket.
invoke-rc.d: unknown initscript, /etc/init.d/docker not found.
invoke-rc.d: could not determine current runlevel
Processing triggers for dbus (1.14.10-4ubuntu4.1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.6) ...
Processing triggers for man-db (2.12.0-4build2) ...


Este es uno de los choques culturales más comunes cuando pasas de un servidor tradicional a un entorno de desarrollo en la nube (como GitHub Codespaces) o a un contenedor.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo systemctl start docker

"systemd" is not running in this container due to its overhead.
Use the "service" command to start services instead. e.g.: 

service --status-all

Este comando es el hermano del anterior (start), pero su función es informativa. Al ejecutar sudo systemctl status docker, le estás preguntando al sistema: "¿Cómo se siente el servicio de Docker? ¿Está corriendo, está detenido o tuvo algún error?".
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo systemctl status docker

"systemd" is not running in this container due to its overhead.
Use the "service" command to start services instead. e.g.: 

service --status-all


Este comando es uno de los más importantes para tu comodidad como desarrollador. Su objetivo es darte permisos permanentes para manejar Docker sin tener que escribir sudo antes de cada comando.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo usermod -aG docker $USER


Este comando es el "Hola Mundo" universal de la computación, pero aplicado a la infraestructura. Es la prueba definitiva de que Docker está vivo, bien instalado y tiene salida a internet.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
17eec7bbc9d7: Pull complete 
Digest: sha256:85404b3c53951c3ff5d40de0972b1bb21fafa2e8daa235355baf44f33db9dbdd
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world:latest


El comando docker run hello-world es el acto de darle vida a la imagen que descargaste en el paso anterior.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/


Este comando es el "historial" o la "bitácora" de tus contenedores. Mientras que el comando simple docker ps solo te muestra los contenedores que están funcionando en este preciso momento, añadirle el flag -a (all) hace que Docker te muestre absolutamente todos, incluso los que ya se detuvieron o "murieron".
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo docker ps -a
CONTAINER ID   IMAGE         COMMAND     CREATED          STATUS                      PORTS     NAMES
f98405762559   hello-world   "/hello"    36 seconds ago   Exited (0) 35 seconds ago             cranky_cannon
24d9cbd53cf5   alpine        "/bin/sh"   7 minutes ago    Exited (0) 7 minutes ago              alpine_container
6d0980dfbd07   alpine        "/bin/sh"   11 minutes ago   Up 11 minutes                         alpine_prueba


Este comando es el que utilizas para descargar Nginx, uno de los servidores web más potentes y utilizados del mundo. Es el "molde" perfecto para servir páginas web o actuar como la puerta de entrada (proxy) de tu proyecto de software.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
206356c42440: Pull complete 
75a1d70aee50: Pull complete 
a9d395129dce: Pull complete 
df9da45c1db2: Pull complete 
18a071c04bd1: Pull complete 
79697674b897: Pull complete 
9eef040df109: Pull complete 
Digest: sha256:bc45d248c4e1d1709321de61566eb2b64d4f0e32765239d66573666be7f13349
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest


Este es el momento en el que transformas tu máquina en un servidor web real. Al ejecutar este comando, has puesto a funcionar Nginx en "segundo plano".
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo docker run -d -p 80:80 nginx
1bad6038e418395a19464e8db1a96db050dbaa708537d8eccd010a4e126ecdeb


Este comando es tu panel de control en tiempo real. A diferencia del comando anterior con -a, aquí solo ves los contenedores que están activos y consumiendo recursos en este momento.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ sudo docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                 NAMES
1bad6038e418   nginx     "/docker-entrypoint.…"   28 seconds ago   Up 28 seconds   0.0.0.0:80->80/tcp, [::]:80->80/tcp   hungry_faraday
6d0980dfbd07   alpine    "/bin/sh"                13 minutes ago   Up 13 minutes                                         alpine_prueba


El comando docker logs es como abrir el "diario de vida" del contenedor. Te permite ver todo lo que ha sucedido dentro desde el momento en que nació, incluso si se está ejecutando en segundo plano (modo -d).
comando:@jhonlenis ➜ /workspaces/practica-docker (main) $ docker logs hungry_faraday
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/03/17 00:26:29 [notice] 1#1: using the "epoll" event method
2026/03/17 00:26:29 [notice] 1#1: nginx/1.29.6
2026/03/17 00:26:29 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19) 
2026/03/17 00:26:29 [notice] 1#1: OS: Linux 6.8.0-1044-azure
2026/03/17 00:26:29 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1024:524288
2026/03/17 00:26:29 [notice] 1#1: start worker processes
2026/03/17 00:26:29 [notice] 1#1: start worker process 29
2026/03/17 00:26:29 [notice] 1#1: start worker process 30


Este comando es idéntico al anterior, pero con una diferencia clave que demuestra que ya estás dominando Docker: has usado el ID corto (1bad) en lugar del nombre del contenedor (hungry_faraday).
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker logs 1bad
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/03/17 00:26:29 [notice] 1#1: using the "epoll" event method
2026/03/17 00:26:29 [notice] 1#1: nginx/1.29.6
2026/03/17 00:26:29 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19) 
2026/03/17 00:26:29 [notice] 1#1: OS: Linux 6.8.0-1044-azure
2026/03/17 00:26:29 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1024:524288
2026/03/17 00:26:29 [notice] 1#1: start worker processes
2026/03/17 00:26:29 [notice] 1#1: start worker process 29
2026/03/17 00:26:29 [notice] 1#1: start worker process 30

# Lab-Contenedores de listas de Docker


El comando docker container ls -a es la versión moderna y más descriptiva de docker ps -a. En las versiones recientes de Docker, se prefiere agrupar los comandos por el objeto que manejan (en este caso, container).
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker container ls -a
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS                      PORTS                                 NAMES
1bad6038e418   nginx         "/docker-entrypoint.…"   4 minutes ago    Up 4 minutes                0.0.0.0:80->80/tcp, [::]:80->80/tcp   hungry_faraday
f98405762559   hello-world   "/hello"                 6 minutes ago    Exited (0) 6 minutes ago                                          cranky_cannon
24d9cbd53cf5   alpine        "/bin/sh"                13 minutes ago   Exited (0) 13 minutes ago                                         alpine_container
6d0980dfbd07   alpine        "/bin/sh"                17 minutes ago   Up 17 minutes                                                     alpine_prueba


El comando docker container inspect es como hacerle una radiografía completa a tu contenedor. Te devuelve un archivo en formato JSON con absolutamente todos los detalles técnicos de su configuración.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker container inspect jenkins
[
    {
        "Id": "a88b99dffd8c2924a3c3d1f8697155b4129e24962b0b24281676dde6e7e60508",
        "Created": "2026-03-17T00:33:35.687203175Z",
        "Path": "/usr/bin/tini",
        "Args": [
            "--",
            "/usr/local/bin/jenkins.sh"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 27225,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2026-03-17T00:33:35.746921967Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:6c9cebd3534e385f90812dbd447e52571569285e497b835bc7826fa3b060f435",
        "ResolvConfPath": "/var/lib/docker/containers/a88b99dffd8c2924a3c3d1f8697155b4129e24962b0b24281676dde6e7e60508/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/a88b99dffd8c2924a3c3d1f8697155b4129e24962b0b24281676dde6e7e60508/hostname",
        "HostsPath": "/var/lib/docker/containers/a88b99dffd8c2924a3c3d1f8697155b4129e24962b0b24281676dde6e7e60508/hosts",
        "LogPath": "/var/lib/docker/containers/a88b99dffd8c2924a3c3d1f8697155b4129e24962b0b24281676dde6e7e60508/a88b99dffd8c2924a3c3d1f8697155b4129e24962b0b24281676dde6e7e60508-json.log",
        "Name": "/jenkins",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "docker-default",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "bridge",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                15,
                61
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "private",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": null,
            "PidsLimit": null,
            "Ulimits": [],
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/interrupts",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware",
                "/sys/devices/virtual/powercap"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "ID": "a88b99dffd8c2924a3c3d1f8697155b4129e24962b0b24281676dde6e7e60508",
                "LowerDir": "/var/lib/docker/overlay2/8492f6077409edb8557ccc8c30d4f2cc5fa72ef279f49e2081c286be63fda551-init/diff:/var/lib/docker/overlay2/ba9e2e01c409401cbbe3b12adbf039563315ad766cbf7687235e4b416bbe0e21/diff:/var/lib/docker/overlay2/2e8b8505f8b073c0786cf6cdde1504b58de0205786cfcfef5c11b198fe3571a7/diff:/var/lib/docker/overlay2/7c2e17f59e5a7438528d984c47f1ae01d18ccd2108d9e25ef5b64b2bbcd834b9/diff:/var/lib/docker/overlay2/d19c7b6105777a56d9116321f2a787a5c000df62629487425c6ec7fc00ae9f1f/diff:/var/lib/docker/overlay2/8d2c8ee2b99aaa83e64ccaf244d53e99ae5aefb640f137bc51a627707f68ed34/diff:/var/lib/docker/overlay2/a9182dfb923b6ed528762ea7229a622dd57a3c8fd1b426add0f6c63efc82c0b7/diff:/var/lib/docker/overlay2/102a3b1c1975b7273f6c2053e6e35869f2daf5b0a5bd7053dfcd5e645e5cf9f9/diff:/var/lib/docker/overlay2/2c9c58dd7d68ddf7274d537d707d4f3a76e3ab3da0e17d2a219de3f672f0f517/diff:/var/lib/docker/overlay2/e2d46a3e48eaea2acda54f11eeccbd569e6889bb56ade0868c18c7cee17b48cc/diff:/var/lib/docker/overlay2/dee9ae7eda1db3cb0e9e08c4b309f601c572d5ea1b19044a957c71702aac05f3/diff:/var/lib/docker/overlay2/7308023696c2c84f545ba7910968e4d88e43bc0bbdb1f68bc9409b66d37308f7/diff:/var/lib/docker/overlay2/23185ebb7b818380f481dfda1123837bdd03ba1bbc987cbe6b3b661f3f754d3e/diff",
                "MergedDir": "/var/lib/docker/overlay2/8492f6077409edb8557ccc8c30d4f2cc5fa72ef279f49e2081c286be63fda551/merged",
                "UpperDir": "/var/lib/docker/overlay2/8492f6077409edb8557ccc8c30d4f2cc5fa72ef279f49e2081c286be63fda551/diff",
                "WorkDir": "/var/lib/docker/overlay2/8492f6077409edb8557ccc8c30d4f2cc5fa72ef279f49e2081c286be63fda551/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [
            {
                "Type": "volume",
                "Name": "378a471d51aed684423d4bd2e7b3b469f3e5192adbddc5f8d444f8693dbe6c66",
                "Source": "/var/lib/docker/volumes/378a471d51aed684423d4bd2e7b3b469f3e5192adbddc5f8d444f8693dbe6c66/_data",
                "Destination": "/var/jenkins_home",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            }
        ],
        "Config": {
            "Hostname": "a88b99dffd8c",
            "Domainname": "",
            "User": "jenkins",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "50000/tcp": {},
                "8080/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/opt/java/openjdk/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "LANG=C.UTF-8",
                "JENKINS_HOME=/var/jenkins_home",
                "JENKINS_SLAVE_AGENT_PORT=50000",
                "REF=/usr/share/jenkins/ref",
                "JENKINS_UC=https://updates.jenkins.io",
                "JENKINS_UC_EXPERIMENTAL=https://updates.jenkins.io/experimental",
                "JENKINS_INCREMENTALS_REPO_MIRROR=https://repo.jenkins-ci.org/incrementals",
                "COPY_REFERENCE_FILE_LOG=/var/jenkins_home/copy_reference_file.log",
                "JAVA_HOME=/opt/java/openjdk"
            ],
            "Cmd": null,
            "Image": "jenkins/jenkins:lts",
            "Volumes": {
                "/var/jenkins_home": {}
            },
            "WorkingDir": "",
            "Entrypoint": [
                "/usr/bin/tini",
                "--",
                "/usr/local/bin/jenkins.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "org.opencontainers.image.description": "The Jenkins Continuous Integration and Delivery server",
                "org.opencontainers.image.licenses": "MIT",
                "org.opencontainers.image.revision": "cd0890e04944be2ad2a03d433d204f8ef888552d",
                "org.opencontainers.image.source": "https://github.com/jenkinsci/docker",
                "org.opencontainers.image.title": "Official Jenkins Docker image",
                "org.opencontainers.image.url": "https://www.jenkins.io/",
                "org.opencontainers.image.vendor": "Jenkins project",
                "org.opencontainers.image.version": "2.541.2"
            }
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "4ee46e422970b64f481c1abd0f198eb3fb3ff5781e78c2fdcff34455e8a036c0",
            "SandboxKey": "/var/run/docker/netns/4ee46e422970",
            "Ports": {
                "50000/tcp": null,
                "8080/tcp": null
            },
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "4b46bc172d3d90628a58f7555e967435b925d9b760b32ff42e530dd7a9cee076",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.4",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "3e:27:15:eb:3e:09",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "MacAddress": "3e:27:15:eb:3e:09",
                    "DriverOpts": null,
                    "GwPriority": 0,
                    "NetworkID": "dd2e933101880c53cc491f648f0744321fb505e3820fada06ac9982a428da5af",
                    "EndpointID": "4b46bc172d3d90628a58f7555e967435b925d9b760b32ff42e530dd7a9cee076",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.4",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DNSNames": null
                }
            }
        }
    }
]


Este comando es la versión "minimalista" o de "solo lectura" de tu lista de contenedores. Es extremadamente útil cuando dejas de ser un usuario manual y empiezas a automatizar tareas con scripts.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker container ls -aq
a88b99dffd8c
1bad6038e418
f98405762559
24d9cbd53cf5
6d0980dfbd07

# Lab-Contenedores en ejecución con listas de Docker


Este comando muestra los contenedores que tienes actualmente en ejecución (activos). En este momento, tu entorno de trabajo tiene una pequeña infraestructura de tres servidores funcionando simultáneamente, cada uno con un propósito distinto.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker ps
CONTAINER ID   IMAGE                 COMMAND                  CREATED          STATUS          PORTS                                 NAMES
a88b99dffd8c   jenkins/jenkins:lts   "/usr/bin/tini -- /u…"   2 minutes ago    Up 2 minutes    8080/tcp, 50000/tcp                   jenkins
1bad6038e418   nginx                 "/docker-entrypoint.…"   10 minutes ago   Up 10 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   hungry_faraday
6d0980dfbd07   alpine                "/bin/sh"                23 minutes ago   Up 23 minutes                                         alpine_prueba


El comando docker ps --filter "name=jenkins" es una herramienta de búsqueda precisa. En lugar de listar todos los contenedores y obligarte a buscar visualmente, le pides a Docker que actúe como un colador y te muestre únicamente el contenedor que coincida con ese nombre.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker ps --filter "name=jenkins"
CONTAINER ID   IMAGE                 COMMAND                  CREATED         STATUS         PORTS                 NAMES
a88b99dffd8c   jenkins/jenkins:lts   "/usr/bin/tini -- /u…"   3 minutes ago   Up 3 minutes   8080/tcp, 50000/tcp   jenkins


Este comando muestra la foto completa de tu infraestructura en Docker en este momento. Al usar la bandera -a (all), no solo ves lo que está funcionando, sino también los rastros de lo que ya hiciste.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker ps -a
CONTAINER ID   IMAGE                 COMMAND                  CREATED          STATUS                      PORTS                                 NAMES
a88b99dffd8c   jenkins/jenkins:lts   "/usr/bin/tini -- /u…"   3 minutes ago    Up 3 minutes                8080/tcp, 50000/tcp                   jenkins
1bad6038e418   nginx                 "/docker-entrypoint.…"   10 minutes ago   Up 10 minutes               0.0.0.0:80->80/tcp, [::]:80->80/tcp   hungry_faraday
f98405762559   hello-world           "/hello"                 12 minutes ago   Exited (0) 12 minutes ago                                         cranky_cannon
24d9cbd53cf5   alpine                "/bin/sh"                19 minutes ago   Exited (0) 19 minutes ago                                         alpine_container
6d0980dfbd07   alpine                "/bin/sh"                23 minutes ago   Up 23 minutes                                                     alpine_prueba

# Laboratorio 4 : Configuración de un contenedor con la imagen mariadb

El comando le ordenó a Docker construir una "unidad de almacenamiento" independiente. Como no tenías el software en tu equipo, Docker lo descargó de la nube (Docker Hub), lo configuró automáticamente con una contraseña de seguridad que tú definiste y lo puso a funcionar de forma silenciosa en la memoria de tu computadora.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker run -d --name some-mariadb -e MYSQL_ROOT_PASSWORD=my-secret-pw mariadb
Unable to find image 'mariadb:latest' locally
latest: Pulling from library/mariadb
01d7766a2e4a: Pull complete 
899bae0d402d: Pull complete 
633047087aaf: Pull complete 
15bc38add3f6: Pull complete 
ab1b7f466f6e: Pull complete 
a4dd30b1fad7: Pull complete 
35c935f50ac0: Pull complete 
2d6698bfc424: Pull complete 
Digest: sha256:b1cb255a9939d28a1856815f0de6046c20c28c21b92a9f2696bc782b247a47ee
Status: Downloaded newer image for mariadb:latest
d6a0abd75de3ccbd7d7c61b165b7aa14657e49225c6ba3c25a5718bdc04ec220


este comando muestra tu infraestructura de microservicios activa. Tienes cuatro "computadoras virtuales" (contenedores) funcionando al mismo tiempo en tu entorno de desarrollo, cada una con un rol distinto.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker ps
CONTAINER ID   IMAGE                 COMMAND                  CREATED          STATUS          PORTS                                 NAMES
d6a0abd75de3   mariadb               "docker-entrypoint.s…"   17 seconds ago   Up 17 seconds   3306/tcp                              some-mariadb
a88b99dffd8c   jenkins/jenkins:lts   "/usr/bin/tini -- /u…"   5 minutes ago    Up 5 minutes    8080/tcp, 50000/tcp                   jenkins
1bad6038e418   nginx                 "/docker-entrypoint.…"   12 minutes ago   Up 12 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   hungry_faraday
6d0980dfbd07   alpine                "/bin/sh"                25 minutes ago   Up 25 minutes                                         alpine_prueba


Este comando es como pedirle a tu base de datos que te muestre su "configuración de identidad" o sus "reglas de juego" internas.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker exec -it some-mariadb env
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=e68998441298
TERM=xterm
MARIADB_ROOT_PASSWORD=mi-contraseña
GOSU_VERSION=1.19
LANG=C.UTF-8
MARIADB_VERSION=1:12.2.2+maria~ubu2404
HOME=/root


Este comando es la forma más rápida y contundente de eliminar un contenedor, sin importar si está encendido o apagado.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker rm -f some-mariadb
some-mariadb


Este comando es la versión completa y funcional para trabajar con bases de datos en un entorno de desarrollo profesional. A diferencia del anterior, este no solo enciende la base de datos, sino que le abre una "ventana" para que puedas conectarte desde fuera.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker run -d -p 3306:3306 --name some-mariadb -e MYSQL_ROOT_PASSWORD=my-secret-pw mariadb
ecaf32f8d903cf19084a58ef70aaffc9039812a3af06abf854b57e1baddf0e7e


este comando muestra que ahora tienes un centro de datos completo funcionando dentro de tu equipo. Tienes la base de datos, el servidor web y el sistema de automatización trabajando juntos.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker ps
CONTAINER ID   IMAGE                 COMMAND                  CREATED          STATUS          PORTS                                         NAMES
ecaf32f8d903   mariadb               "docker-entrypoint.s…"   18 seconds ago   Up 17 seconds   0.0.0.0:3306->3306/tcp, [::]:3306->3306/tcp   some-mariadb
a88b99dffd8c   jenkins/jenkins:lts   "/usr/bin/tini -- /u…"   15 minutes ago   Up 15 minutes   8080/tcp, 50000/tcp                           jenkins
1bad6038e418   nginx                 "/docker-entrypoint.…"   22 minutes ago   Up 22 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp           hungry_faraday
6d0980dfbd07   alpine                "/bin/sh"                35 minutes ago   Up 35 minutes                                                 alpine_prueba

# Practicas-Retos

# Practica-Búsqueda de imágenes del repositorio


Este comando es la forma de asegurar que tienes la versión más reciente del servidor web Nginx en tu equipo local antes de empezar a trabajar.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
Digest: sha256:bc45d248c4e1d1709321de61566eb2b64d4f0e32765239d66573666be7f13349
Status: Image is up to date for nginx:latest
docker.io/library/nginx:latest


Este comando es una herramienta de filtrado rápida para ver los detalles técnicos de una imagen específica sin tener que leer toda la lista de tu inventario.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker images | grep nginx
nginx             latest    99133eed2307   6 days ago     161MB


Este comando confirma que tienes en tu sistema la imagen de Alpine Linux, que es la navaja suiza de los desarrolladores de software por ser increíblemente ligera y rápida.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker pull alpine
Using default tag: latest
latest: Pulling from library/alpine
Digest: sha256:25109184c71bdad752c8312a8623239686a9a2071e8825f20acb8f2198c3f659
Status: Image is up to date for alpine:latest
docker.io/library/alpine:latest


Con este comando has descargado el "molde" de Ubuntu, que es uno de los sistemas operativos Linux más populares y potentes del mundo. A diferencia de Alpine, Ubuntu viene con muchas más herramientas preinstaladas, lo que lo hace ideal para entornos de desarrollo complejos.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
01d7766a2e4a: Already exists 
Digest: sha256:d1e2e92c075e5ca139d51a140fff46f84315c0fdce203eab2807c7e495eff4f9
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest


Este comando te muestra tu inventario de imágenes actual. Es el catálogo de "moldes" que tienes descargados en tu máquina para crear contenedores cuando los necesites.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker images
REPOSITORY        TAG       IMAGE ID       CREATED        SIZE
nginx             latest    99133eed2307   6 days ago     161MB
jenkins/jenkins   lts       6c9cebd3534e   3 weeks ago    486MB
mariadb           latest    2bb31c7c9ec5   3 weeks ago    336MB
ubuntu            latest    bbdabce66f1b   4 weeks ago    78.1MB
alpine            latest    a40c03cbb81c   6 weeks ago    8.44MB
hello-world       latest    1b44b5a3e06a   7 months ago   10.1kB

# Practica-Despliegue de batallas espaciales dockerizadas


Este comando ha puesto en marcha un nuevo servidor web independiente, funcionando en paralelo a los que ya tenías. Es la forma clásica de desplegar servicios web usando Docker.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker run -d --name mi-servidor-nginx -p 8080:80 nginx
edc57bc6da73a0e0c78b6a596f2bbc4886dd4d489b65d679391df25b6c7f4988


este comando muestra tu ecosistema de microservicios en pleno funcionamiento. Tienes una infraestructura completa y balanceada para desarrollar tu proyecto.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker ps
CONTAINER ID   IMAGE                 COMMAND                  CREATED          STATUS          PORTS                                         NAMES
edc57bc6da73   nginx                 "/docker-entrypoint.…"   15 seconds ago   Up 15 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp       mi-servidor-nginx
ecaf32f8d903   mariadb               "docker-entrypoint.s…"   4 minutes ago    Up 4 minutes    0.0.0.0:3306->3306/tcp, [::]:3306->3306/tcp   some-mariadb
a88b99dffd8c   jenkins/jenkins:lts   "/usr/bin/tini -- /u…"   19 minutes ago   Up 19 minutes   8080/tcp, 50000/tcp                           jenkins
1bad6038e418   nginx                 "/docker-entrypoint.…"   26 minutes ago   Up 26 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp           hungry_faraday
6d0980dfbd07   alpine                "/bin/sh"                40 minutes ago   Up 40 minutes                                                 alpine_prueba


Este comando ha creado lo que podríamos llamar un "contenedor de espera" o de larga duración. Es una técnica muy usada cuando necesitas que un contenedor se mantenga encendido para realizar tareas de mantenimiento o para que sirva como puente de red sin ejecutar un servidor pesado.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker run -d --name alpine-seguro alpine sleep 3600
842fd008bb56f5cc5511929f97604df827451b50b51278307332f97187de2166

# Practica-Docker Container Identification


Este comando es una técnica avanzada de automatización y gestión de datos. En lugar de solo mirar la información en la terminal, has extraído los datos clave de tus contenedores y los has guardado en un archivo permanente.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker ps --format "{{.ID}} {{.Image}} {{.Names}}" > containers.txt


Este comando te permite ver el contenido del archivo que acabas de crear. Al ejecutar cat containers.txt, has verificado que tu reporte de infraestructura se generó correctamente y está bien organizado.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ cat containers.txt
842fd008bb56 alpine alpine-seguro
7c92d11c3ac9 alpine contenedor-alpine
edc57bc6da73 nginx mi-servidor-nginx
ecaf32f8d903 mariadb some-mariadb
a88b99dffd8c jenkins/jenkins:lts jenkins
1bad6038e418 nginx hungry_faraday
6d0980dfbd07 alpine alpine_prueba 


Este comando es un excelente ejemplo de filtrado selectivo y exportación. Es una evolución del reporte anterior, pero mucho más profesional porque incluye encabezados de tabla y se enfoca en un solo servicio.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ docker ps --filter "ancestor=jenkins/jenkins" --format "table {{.ID}}\t{{.Image}}\t{{.Names}}" > container_jenkins.txt


Este comando te permite verificar el contenido del reporte específico que generaste para Jenkins. Sin embargo, hay un detalle técnico muy importante que notar en el resultado: el archivo solo contiene los encabezados.
comando: @jhonlenis ➜ /workspaces/practica-docker (main) $ cat container_jenkins.txt
CONTAINER ID   IMAGE     NAMES