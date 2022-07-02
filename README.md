A self managed gitlab instance at my localhost.
===

### Tools:

- Using `docker compose` to manage the services.

### Services:

- Gitlab Instance (of course)
- Gitlab Runner

> Runner is like a machine that can run jobs.

### Register a gitlab runner:

`docker exec -it gitlab-runner gitlab-runner register`

---

> host: http://gitlab-ce (This is the _container_name_ of the gitlab instance - see in [compose](docker-compose.yml) file).

> token: `token`

> runner name: `anything`

> tags: `whatever` (you will need to use these tags in your job stages)

> description: `whatever`

---

