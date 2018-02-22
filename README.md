# Portainer stack

## Requirements

* Docker Engine
* Docker Compose

## Usage

* Start: `bash start`
* Stop: `bash stop`
* Default password: test12345678

## Generate password

* Option 1

```shell
PASSWORD=my_password_here
docker run --rm httpd:2.4-alpine htpasswd -nbB admin $PASSWORD | cut -d ":" -f 2
```

* Option 2

```shell
PASSWORD=my_password_here
htpasswd -nb -B admin $PASSWORD | cut -d ":" -f 2
```

---

* More info: https://portainer.readthedocs.io/en/stable/configuration.html#admin-password
