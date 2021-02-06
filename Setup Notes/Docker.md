Docker Setup Note
========================================================================

Installation
------------------------------------------------------------------------

See https://docs.docker.com/install/linux/docker-ce/centos/.

Configuration
------------------------------------------------------------------------

### Proxy Configuration

```bash
mkdir -p /etc/systemd/system/docker.service.d
vim /etc/systemd/system/docker.service.d/http-proxy.conf
```

```
[Service]
EnvironmentFile=/etc/environment
```

### Daemon Configuration

```bash
vim /etc/docker/daemon.json
```

```
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "100m"
  },
  "registry-mirrors": ["http://DOCKER_REGISTRY_MIRROR/"],
  "insecure-registries": ["http://DOCKER_REGISTRY_MIRROR/"]
}
```

See also:

 * https://docs.docker.com/config/daemon/systemd/
 * https://docs.docker.com/registry/recipes/mirror/
 * https://docs.docker.com/registry/insecure/
 * https://docs.docker.com/config/containers/logging/json-file/
 * https://docs.docker.com/engine/reference/commandline/dockerd/
 
Client configuration
------------------------------------------------------------------------

```bash
mkdir -p /root/.docker
vim /root/.docker/config.json
```

```
{
  "proxies": {
    "default": {
      "httpProxy": "http://HOST:PORT",
      "httpsProxy": "http://HOST:PORT",
      "ftpProxy": "http://HOST:PORT",
      "noProxy": "NO_PROXY_HOSTS"
    }
  }
}
```

See also:

 * https://docs.docker.com/network/proxy/
 
Reload & Restart
------------------------------------------------------------------------

```bash
systemctl daemon-reload
systemctl restart docker
```

See also:

 * https://docs.docker.com/compose/install/
