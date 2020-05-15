# home-proxy
A ready to go docker-compose configuration for a proxy service including letsencrypt support.

## Usage
- Clone repository: `git clone https://github.com/muyajil/home-proxy.git`
- Create `.env` file from template `mv .env_template .env`
- Replace values in `.env` with values corresponding to your setup
- Run: `docker-compose up -d`

## Make a container available through this proxy
- The container needs to join the network:
```
services:
  some-service:
    networks:
      - base-network
```
      VIRTUAL_HOST: ombi.srv.ajil.ch
      LETSENCRYPT_HOST: ombi.srv.ajil.ch
      PROXY_LOCATION: ombi
      VIRTUAL_PORT: 3579
- The container needs the following environment variables to be set:
  - `VIRTUAL_HOST`: The domain under which the container should be available
  - `LETSENCRYPT_HOST`: Same as above
  - `PROXY_LOCATION`: The address under which the proxy finds the container in `base-network`. This is usually just the name of the service.
  - `VIRTUAL_PORT`: Under which port does the container offer the service.
