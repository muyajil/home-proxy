# proxy
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
  networks:
    base-network:
      external: true
```
- The container needs the following environment variables to be set:
  - `VIRTUAL_HOST`: The domain under which the container should be available
  - `LETSENCRYPT_HOST`: Same as above
  - `VIRTUAL_PORT`: Under which port does the container offer the service.
