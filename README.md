Liferay Portal 7.0 CE GA5 on Tomcat with mysql DB (two containers)
==========================================================

Dockerfile based on ctliv/liferay:6.2

Image available in docker registry: https://hub.docker.com/r/bfreire/liferay/

## How to use this image
### Launch it using "docker run":

```
# Run mysql:
docker run --name lep-db -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_USER=lportal -e MYSQL_PASSWORD=lportal -e MYSQL_DATABASE=lportal -d mysql

# To enable remote connection add option:
#     -p 3306:3306


# Run liferay:
docker run --name lep-as -p 80:8080 -p 443:8443 --link lep-db -d bfreire/liferay

# To enable development mode add options (includes SSH daemon + JMX monitoring + dt_socket debugging) add options:
#     -e LIFERAY_DEBUG=1 -p 2222:22 -p 1099:1099 -p 8999:8999

# If docker daemon does not run on localhost (e.g.: VirtualBox), JMX monitoring needs option:
#     -e VM_HOST=<docker daemon hostname>

# To mount liferay deploy directory locally add:
#     -v /absolute/path/to/local/folder:/var/liferay/deploy
```

### Launching using "docker-compose":

```
git clone https://github.com/bfreire/docker-liferay-mysql
cd docker-liferay-mysql
docker-compose up
# For production mode use: docker-compose -f docker-compose-prod.yml up
```

### Use:
Point browser to docker machine ip (port 80 or port 443)

### If you want to run an hypersonic db instead of mysql, don't need to run none of the steps above. Just run with the following tag:

```
docker run -p 80:8080 -p 443:8443 -d bfreire/liferay:hypersonic
```
