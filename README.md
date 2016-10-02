
# The Synereo Social Platform

#### [WARNING]

This is an **experimental**, pre-release software and should be used **for testing purposes only**. While the software is in pre-release phase, there is a **high likelihood of data loss** and **features will change** without notice.

## Prerequisites
* Basic knowledge of [Docker](https://www.docker.com)
  * New users should start [here](https://docs.docker.com/engine/understanding-docker/)
* A machine capable of running [Docker](https://www.docker.com), with at least 4 GB RAM (> 8 GB recommended)
  * For Linux users, installation information is [available here](https://docs.docker.com/engine/installation/linux)
  * For Mac users, system requirements and installation information is [available here](https://docs.docker.com/docker-for-mac/)
  * For Windows users, system requirements and installation information is [available here](https://docs.docker.com/docker-for-windows/) or you can try using Docker Tool Box [available here](https://www.docker.com/products/docker-toolbox) (This includes Kitematic, UI interface to mange images and containers)

  [CAUTION] Based on our experience, Docker may not perform as intented on Windows 7 home version machines

## Installation

Please make sure Docker is running and open command prompt for Docker ("CLI", Kitematic -> "Docker CLI" lower left hand corner).

### Build docker image using
```
# docker build -t synereo-node https://raw.githubusercontent.com/synereo/dockernode/single/Dockerfile
```

The build process will take 10-30 minutes depending on your machine and network connection. It will download approximately  750 MB of data.

### Running standalone node
After the build completes, run the following command (First time usage) to create a Docker container named `synereo-node-01`:
```
# docker run -itd -p 443:9876 -h mynodehost --dns 8.8.8.8 --name synereo-node-01 synereo-node
```

## Accessing the Synereo Social Platform

To access the application, you must first know Docker IP address  and default installation on different OS has the following IP's:

OS|Docker Version |Default IP
--------|--------|--------
Mac OSX| Prior 1.12 alpha | 192.168.99.100
Mac OSX| 1.12 alpha | 127.0.0.1 or localhost
Windows 8/8.1| - | 192.168.99.100 or localhost
Windows 10| - | 192.168.99.100 or locahost
Linux | - | 172.17.0.1



On Linux and Windows machines, you can get the IP address of your running container with the following command:

```
# docker inspect --format '{{ .NetworkSettings.IPAddress }}' synereo-node-01
```

You can then access the application with your web browser at:
```
https://<IP address>/ for example: https://192.168.99.100/
```

**NOTE**: When accessing the application for the first time, your browser will warn you that the site is insecure.  This happens because the pre-release version of this software uses a self-signed TLS certificate.  You should follow your browser's instructions about approving the site's certificate (Usually, click to "Advanced" option and accept the certificate).

**Congratulations!**, you can now log in using the administrator account:

Username|Password
--------|--------
admin@localhost|a

After successful login, there may be a delay before you can see blockchain wallet address in "About" screen.

**NOTE**: This username and password can be changed by editing the `eval.conf` file inside the running container. Information on how to do this will be made available shortly.

## Stopping the Container

To stop the container:

```
# docker stop synereo-node-01
```

## General Usage

To restart the container:

```
# docker start synereo-node-01
```

## Further Help

Please visit the `#docker-testing` channel on [our Slack](https://slack.synereo.com).
