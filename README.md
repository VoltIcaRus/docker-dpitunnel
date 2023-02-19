# docker-dpitunnel

[python-proxy](https://github.com/qwj/python-proxy) + [DPITunnel-cli](https://github.com/zhenyolka/DPITunnel-cli)

## Usage

```yaml
version: '2.4'

x-common-env: &default-env

x-common-key: &default-key
  restart: always
  security_opt:
    - no-new-privileges:true
  logging:
    driver: json-file
    options:
      max-size: "1024k"
      max-file: "5"

services:
  dt:
    <<: *default-key
    container_name: dt
    image: ghcr.io/by275/dpitunnel:latest
    network_mode: bridge
    ports:
      - 8008:8008
      - 21000:8080
    environment:
     
      PROXY_USER: " "
      PROXY_PASS: " "
      PROXY_PORT: 8008
      DT_PORT: 8080   
      PROXY_VERBOSE: "true"
      DT_USER_OPTS: "--desync-attacks split_fake --ttl 1"
      DT_DOH: "true"

```


