## Staging/Production Deployer

The deployer for flyboat is a custom FastAPI application [zip-deployer](https://github.com/PythonCoderAS/zip-deployer). It takes the secret key and the zipfile to deploy (see more at [the docs](https://flyboat-dev.biishop.org/docs)). The deployed data can be viewed at https://<name_of_zip_file>.flyboat-dev.biishop.org. If a zip file with name `main.zip` is sent, then it gets deployed to the main site (https://flyboat.biishop.org). The application expects HTTP responses at port `8020`.

### Getting the secret key

The secret key can be gotten by asking @biishop. The secret key is also provided as the Github Actions secret `DEPLOY_KEY`. 

### Updating zip-deployer to the latest version
The zip-deployer directory is stored under `/srv/zip-deployer`. To pull in the latest commit, run:
```shell
git pull
```

There is a shell script (`redeploy.sh`) that will rebuild and recreate the Docker container for the deployer. You can run it by pasting `/srv/zip-deployer/redeploy.sh`. If you wish to do it manually, the contents of the shell script are below:

```shell
#!/bin/bash
sudo docker build -t zip-deployer .
sudo docker container stop zip-deployer
sudo docker container rm zip-deployer
sudo docker run --name zip-deployer --detach -p 8020:8000 -v /srv/staging:/directory --restart unless-stopped zip-deployer
```