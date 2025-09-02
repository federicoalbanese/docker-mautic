# Mautic FPM + Nginx Template

This directory provides a FPM + Nginx setup to run [Mautic](https://www.mautic.org/) using Docker Compose. It uses the official fpm-based Mautic Docker image and includes MySQL for storage and Nginx for frontend.

> [!IMPORTANT]
> **Security Notice:**
> Be sure to change the `MYSQL_PASSWORD` and `MYSQL_ROOT_PASSWORD` environment variables under [.env](.env) before deploying to production.

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/mautic/docker-mautic.git
   cd docker-mautic/examples/fpm-nginx
   ```

2. Start the environment:

   ```bash
   docker compose up -d
   ```

3. Access Mautic in your browser at:
   [http://localhost:8080](http://localhost:8080)

## Local development

For a development setup that mounts the Mautic source code directly and
matches container permissions with your host user, use the
`docker-compose.local.yml` file.

1. Download Mautic 6.0.4 into a `mautic` directory placed next to this
   compose file.
2. Set `LOCAL_UID` and `LOCAL_GID` in `.env` to your host user's UID and GID.
3. Launch the stack with:

   ```bash
   docker compose -f docker-compose.local.yml up -d
   ```

This configuration is intended for local development only. Create separate
compose files for staging and production environments.

## Configuration

You can configure environment variables in the [.env](.env) file. **Make sure to update the following before deploying to production:**

```yaml
MYSQL_PASSWORD=mautic_db_pwd
MYSQL_ROOT_PASSWORD=changeme
```

You may also want to map volumes or adjust ports as needed.

## Cleanup

To stop and remove the containers:

```bash
docker compose down
```

To remove all volumes (this will delete your data):

```bash
docker-compose down -v
```

## 📘 Resources

* [Mautic Documentation](https://docs.mautic.org/)
* [Mautic Docker GitHub](https://github.com/mautic/docker-mautic)
