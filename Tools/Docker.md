# Docker
## Docker
```bash
> docker info
...
 Docker Root Dir: /var/lib/docker
...

> docker images
REPOSITORY               TAG                 IMAGE ID            CREATED             SIZE
<none>                   <none>              3f185513a38d        6 days ago          778MB
domino-regression-none   latest              10f8ad66c529        6 days ago          2.06GB
...
```

## Docker-compose
https://learnxinyminutes.com/docs/yaml/
```yaml
version: "3.4"

# define some optional helpers
x-build: &default-build # define anchor (anchored_content: &anchor_name)
  context: . # define the path to a directory containing a Dockerfile, or a url to a git repository
  args:
    - UID=1000
    - GID=1000
x-volumes: &default-volumes
  - '${HOME}:${HOME}'

# define the docker images
services:
  dev:
    build: *default-build # inject anchor content (other_anchor: *anchor_name)
    image: dev-${USER}
    privileged: true
    volumes: *default-volumes
    working_dir: ${HOME}
    environment:
      - HOME=${HOME}
  notes:
    build:
      << : *default-build # merge maps into a single map (Merge Key Language-Independent Type)
      dockerfile: Dockerfile-notes # use an alternate Dockerfile
    image: notes-${USER}
    privileged: true
    volumes: *default-volumes
    working_dir: ${HOME}
    environment:
      - HOME=${HOME}
```

```bash
> docker-compose build --pull <name>
```
