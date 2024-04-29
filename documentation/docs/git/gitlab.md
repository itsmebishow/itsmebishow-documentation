gitlab

---

Containerization is an OS-level virtualization method used to deploy and run distributed applications without launching an entire Virtual Machine (VM) for each application.

It is a kind of OS virtualization where we run our applications in a separate `user space` called ==containers==.

## Docker Networking

By default, during installation, the Docker Engine creates three networks for you:

```bash title="bash"
$ docker network ls
```

When Docker spins up a new container, by default, it creates a network stack for the container and attaches to the default bridge network. However, optionally, you could attach the container to the host or none network.

Docker provides a `docker inspect` subcommand, which is as handy as a Swiss Army knife, to dive deep into the low-level details of the Docker `container` or `image`.

---

## Reference

- []()