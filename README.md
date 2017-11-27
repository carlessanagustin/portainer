# Portainer stack

## Requirements

* Docker Engine
* Docker Compose

## Usage: Docker Compose

* Create & start: `./create_start.sh`
* Start: `./start.sh`
* Stop: `./stop.sh`

## Usage: Shell script

https://portainer.readthedocs.io/en/stable/configuration.html#admin-password

```shell
PASSWORD=my_password_here
PASS=$(docker run --rm httpd:2.4-alpine htpasswd -nbB admin $PASSWORD | cut -d ":" -f 2)
# or htpasswd -nb -B admin <password> | cut -d ":" -f 2

docker volume create portainer_data
docker run -d -p 9000:9000 \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -V portainer_data:/data \
    - ./certs:/certs \
    portainer/portainer --admin-password $PASS --ssl --sslcert /certs/https.crt --sslkey /certs/https.key
```
