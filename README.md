# Description
This image based on alpine and contained the tower-cli.

# Usage

```bash
docker run -v $(pwd)/tower_cli.cfg:/root/.tower_cli.cfg -t adito/ansible-tower-cli sh -c "tower-cli version"
```
**Output**
```bash
Tower CLI 3.2.1
API v2
AWX 1.0.3.41
Ansible 2.4.3.0
```

## Tower Cli configuration
```
# User options (set with `tower-cli config`; stored in ~/.tower_cli.cfg).
host: http://tower-cli.example.com
username: admin
password: password
verify_ssl: False

# Defaults.
use_token: False
verbose: False
certificate:
format: human
color: True
description_on: False
```

# Git runner
We've created this to start a ansible tower job through gitrunner
Gitrunner config (config.toml)

```toml
[[runners]]
  name = "ansible.runner"
  url = "https://gitintern.example.com/"
  token = "TOCKEN"
  executor = "docker"
  build_dir = "/gitdata"
  environment = ["GIT_SSL_NO_VERIFY=1"]
  [runners.docker]
    image = "adito/ansible-tower-cli"
    privileged = false
    disable_cache = true
```
