Liferay Portal 7.0 CE GA5 on Tomcat with HSQLDB2 (Hyper SQL Database)
==========================================================

Dockerfile based on ctliv/liferay:6.2

Image available in docker registry: https://hub.docker.com/r/bfreire/liferay/

## Pulling:

```
docker pull bfreire/liferay:hsqldb2
```

## Launching using "docker run":

```
# Run liferay:
docker run --name lep-as -p 80:8080 -p 443:8443 -d bfreire/liferay:hsqldb2

# To enable development mode add options (includes SSH daemon + JMX monitoring + dt_socket debugging) add options:
#     -e LIFERAY_DEBUG=1 -p 2222:22 -p 1099:1099 -p 8999:8999

# If docker daemon does not run on localhost (e.g.: VirtualBox), JMX monitoring needs option:
#     -e VM_HOST=<docker daemon hostname>

# To mount liferay deploy directory locally add:
#     -v /absolute/path/to/local/folder:/var/liferay/deploy
```

## Use:
Point browser to docker machine ip (port 80 or port 443)
