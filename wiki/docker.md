## Docker
Docker powers many of the applications, including the authentication server. Note that to run any docker command `sudo` has to be prefixed to the command. For example, if you want to run `docker run some_app`, it needs to be `sudo docker run some_app`.

### Auto-restarting new containers
When making new containers through `docker run`, please make sure that `--restart unless-stopped` is always provided. Otherwise, if the system is restarted as part of routine maintainence, the container will be stopped and will not restart.

### List of Docker applications
These are some of the applications being run in Docker containers.
- [Logto](logto)
- [Frontend Deployer](deployer)