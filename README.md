# Postgres + PGAdmin using docker-compose

This project sets up a PostgreSQL database container (`postgres`) alongside a pgAdmin4 container (`pgadmin`) for easy web-based administration.

## Prerequisites

* Docker installed and running (https://docs.docker.com/engine/install/)
* Docker Compose installed and running (https://docs.docker.com/compose/install/)

## Environment Variables

This docker-compose.yml file utilizes environment variables to customize configurations. You can set these variables before running commands:

* `USERNAME`: Username for the PostgreSQL database (defaults to `root`)
* `PASSWORD`: Password for the PostgreSQL database (defaults to `1`) - Consider using a more secure password!
* `PORT`: Port to expose the PostgreSQL container (defaults to `5432`)
* `PGADMIN_PORT`: Port to expose the pgAdmin4 container (defaults to `7100`)
* `TZ`: Timezone for the PostgreSQL container (defaults to `Asia/Tehran`) - Adjust this to your desired location

**Recommendation:** It's highly recommended to use a stronger password for `PASSWORD` and store it securely using a secrets management tool, not directly in the environment variable.

## Usage

1. **Create a `.env` file (optional):**
    - Create a file named `.env` in the same directory as your `docker-compose.yml` file.
    - Add environment variable definitions in the format `KEY=VALUE`, one per line. For example:

      ```
      USERNAME=myuser
      PASSWORD=strong_password
      PORT=5433
      PGADMIN_PORT=8080
      TZ=America/Los_Angeles
      ```

2. **Start the services:**

   ```bash
   docker-compose up -d
   ```
This will create and start both the postgres and pgadmin containers in detached mode (background).

3. **Access pgAdmin4:**

   - Open your web browser and navigate to `http://localhost:<PGADMIN_PORT>`, replacing `<PGADMIN_PORT>` with the port you configured (default: `7100`).
   - Login using the credentials:
      - Username: `admin@admin.com`
      - Password: `admin` **(Change this to a strong password!)**
## Configuration
- **Environment Variables:** As mentioned earlier, you can customize settings by overriding environment variables.
- **Volumes:** The postgres service uses a named volume named postgres to persist database data. This ensures data isn't lost when containers are recreated.
- **Health Checks:** The postgres service defines health checks to monitor its status.
## Stopping and Removing Services
- Stop:

```Bash
docker-compose stop
```
- Remove:

```Bash
docker-compose down
```
