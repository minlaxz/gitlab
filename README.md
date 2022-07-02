A self managed gitlab instance at my localhost.
===

> A breifly describing of the `how-I-did`.

### ~~~ Tools:

- Using `docker compose` to manage the services.

### ~~~ Services:

- Gitlab Instance (of course)
- Gitlab Runner

> Runner is like a machine that can run jobs.

---

## Start the services

```bash
docker-compose up -d
```

### ~~~ Check the gitlab instance is healthy

```bash
docker-compose exec gitlab /bin/bash -c "gitlab-ctl status"

# OR

watch -n 1 docker compose ps
```

---

## Configure the gitlab instance for the first time

### ~~~ Getting the root password
```bash
docker exec -it gitlab-ce cat /etc/initial_root_password
```

### ~~~ Sign in @ [localhost]()

username: root

password: [root-password]

### ~~~ Change the admin credentials
- Change the username root to something else
- Change the password to something else

---

## Register a gitlab runner:

```bash
docker exec -it gitlab-runner gitlab-runner register
```


> host: http://gitlab-ce (This is the _container_name_ of the gitlab instance - see in [compose](docker-compose.yml) file).

> token: `token`

> runner name: `anything`

> tags: `whatever` (you will need to use these tags in your job stages)

> description: `whatever`

---

