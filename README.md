Docker Hub: https://hub.docker.com/repository/docker/lrstry/odoo13-latest-ptvsd

The changes I did to this fork:

- Offer only ODOO 13.0, with 'latest' version
- Add ptvsd to image and implement attach-hook for remote debugging

Setup:

```shell
docker pull lrstry/odoo13-latest-ptvsd
docker run -d -p 5432:5432 -e POSTGRES_USER=odoo -e POSTGRES_PASSWORD=odoo -e POSTGRES_DB=postgres --name db postgres:10
docker run -p 8069:8069 -p 3000:3000 -v /Users/lrstry/Documents/SwaF/custom_swaf:/mnt/extra-addons --name odoo --link db:db -t lrstry/odoo13-latest-ptvsd
```

Debugging with VSCode using following launch.json:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Python: Remote Attach",
      "type": "python",
      "request": "attach",
      "port": 3000,
      "debugServer": 3000,
      "host": "localhost",
      "pathMappings": [
        {
          "localRoot": "{path to local addons folder}",
          "remoteRoot": "/mnt/extra-addons/"
        }
      ]
    }
  ]
}
```
