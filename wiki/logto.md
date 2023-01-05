## Logto

Logto is deployed via [docker](docker). 

### Updating to the latest version

```
sudo docker pull ghcr.io/logto-io/logto:prerelease
sudo docker container stop logto
sudo docker container rm logto
sudo docker run --name logto --network host --restart unless-stopped -e TRUST_PROXY_HEADER=1 -e ENDPOINT=https://auth.flyboat.biishop.org -e DB_URL=postgres://logto:logto@127.0.0.1:5432/logto ghcr.io/logto-io/logto:prerelease # Do! not! change! the! environment! variables!
```
