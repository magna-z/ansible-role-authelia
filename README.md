authelia
---

Configure and run unprivileged Authelia server as docker container into systemd.service.


### Links
- <https://authelia.com>
- <https://github.com/authelia/authelia>
- <https://hub.docker.com/r/authelia/authelia>


### Variables
- **`authelia_docker_image`** *(type=string, default="...:latest")* - Docker image for using into systemd.service.

- **`authelia_docker_network`** *(type=string, default="bridge")* - Connect a container to a network as `docker run --network=...`.
- **`authelia_docker_publish_ports`** *(type=list, default=["127.0.0.1:9091:9091", "127.0.0.1:9092:9092"])* - List of strings with publish a container’s ports to the host as `docker run --publish=...`.

- **`authelia_docker_envs`** *(type=list, default=[])* - List of objects in format `{KEY: value}` for set environment variables as `docker run --env=...`.
- **`authelia_docker_labels`** *(type=list, default=[])* - List of objects in format `{key: value}` for set meta data on a container as `docker run --label=...`.

- **`authelia_main_config`** *(type=string, mandatory)* - Multiline string with content for main config (`/etc/authelia/config.yml`).  
  See <https://github.com/authelia/authelia/blob/master/config.template.yml>.
- **`authelia_extra_config_files`** *(type=list, default=[])* - List of objects in format `{filename: "", content: ""}`, where `filename` - name of file in `/etc/authelia/` and `content` - multiline string with config file content.


### Examples
```yaml
authelia_docker_image: authelia/authelia:4.37.5
authelia_docker_network: host
authelia_main_config: |
    # see https://www.authelia.com/configuration/identity-providers/open-id-connect/

authelia_extra_config_files:
  - filename: users.yml
    content: |
      # see https://www.authelia.com/reference/guides/passwords/
```
