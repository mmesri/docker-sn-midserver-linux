# What is ServiceNow MID Sever

[Read here](https://docs.servicenow.com/bundle/paris-servicenow-platform/page/product/mid-server/concept/mid-server-landing.html)

Why do you need it? Just ignore this repo if you don't know the answer.

# TLDR

`mmesri/snow_mid_docker:linux`

## Get started right away

```bash
$ docker run -d --name sn-mid-server \
  -e 'SN_URL=https://dev00000.service-now.com' \
  -e 'SN_USER=username' \
  -e 'SN_PASSWD=userpassword' \
  -e 'SN_MID_NAME=sn-mid-server' \
  mmesri/snow_mid_docker:linux
```

```
Optional Parameters:
SN_MID_NAME_STATIC      (If TRUE, do not append random UUID to end of MID Server Name)
SN_MAX_THREADS          (Set max thread count in MID Server Parameters)
SN_JVM_SIZE             (Sets the JVM Size in MB)
SN_PROXY_HOST           (Sets required proxy host)
SN_PROXY_PORT           (Sets the required proxy port)
SN_PROXY_USERNAME       (Sets required proxy username)
SN_PROXY_PASSWORD       (Sets the required proxy password)
```

or using Docker Compose:

```yaml
version: '3'
services:
  midserver:
    container_name: sn-midserver
    image: mmesri/snow_mid_docker:linux
    network_mode: host
    environment:
      - SN_URL=https://dev00000.service-now.com
      - SN_USER=username
      - SN_PASSWD=password
      - SN_MID_NAME=my-mid-server
```

# Persisting Logs

```bash
$ docker run -d --name sn-mid-server \
  -e 'SN_URL=https://dev00000.service-now.com' \
  -e 'SN_USER=username' \
  -e 'SN_PASSWD=password' \
  -e 'SN_MID_NAME=my-mid-server' \
  -v './sn-midserver/logs:/opt/agent/logs' \
  mmesri/snow_mid_docker:linux
```

or using Docker Compose:

```yaml
version: '3'
services:
  midserver:
    container_name: sn-midserver
    image: mmesri/snow_mid_docker:linux
    volumes:
      - ./sn-midserver/logs:/opt/agent/logs
    network_mode: host
    environment:
      - SN_URL=https://dev00000.service-now.com
      - SN_USER=username
      - SN_PASSWD=password
      - SN_MID_NAME=my-mid-server
```
