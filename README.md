A self managed gitlab instance at my localhost.
===

> A breifly describing of the `how-I-did`.

### > Tools

- Using `docker compose` to manage the services.

### > Services

- Gitlab Instance (of course)
- Gitlab Runner

> Runner is like a machine that can run jobs.

---

## Start the services

```bash
docker-compose up -d
```

### > Check the gitlab instance is healthy

```bash
docker-compose exec gitlab /bin/bash -c "gitlab-ctl status"

# OR

watch -n 1 docker compose ps
```

---

## Configure the gitlab instance for the first time

### > Getting the root password
```bash
docker exec -it gitlab-ce cat /etc/initial_root_password
```

### > Sign in @ [localhost]()

username: root

password: [root-password]

### > Change the admin credentials
- Change the username root to something else
- Change the password to something else

### > Create a new project for whatever you want
...

---

## Register a gitlab runner:

```bash
docker exec -it gitlab-runner gitlab-runner register
```

`gitlab-ce` is the _container_name_ of the gitlab instance - see in [compose](docker-compose.yml) file #L7

> host: http://gitlab-ce 

Two type of tokens for runners
- Shared runner
- Project specific runner
> token: `token`

> runner name: `anything`

you will need to use these tags in your job stages
> tags: `whatever` 

> description: `whatever`

> executor: `docker`

See the services tag in [gitlab-ci.yml](.gitlab-ci.yml)

I am going to use dind (docker in docker) so set the image
> docker-image: `docker:20.10.16`

We are using DIND so we need to set the privileged flag
> After registering the runner, you need to set the flag `privileged = true`
---

