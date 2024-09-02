# Flask App with Docker, Gunicorn, and Nginx

This project sets up a simple Flask application served with Gunicorn and reverse-proxied with Nginx, all managed via Docker Compose. The application is configured to use HTTPS with a self-signed certificate.

## Project Structure

- `app.py`: The Flask application.
- `requirements.txt`: Python dependencies for the Flask app.
- `Dockerfile`: Dockerfile to build the Flask app image.
- `nginx/`
  - `default.conf`: Nginx configuration file (configured for HTTPS).
  - `Dockerfile`: Dockerfile to build the Nginx image.
  - `selfsigned.crt`: Self-signed SSL certificate.
  - `selfsigned.key`: Private key for the SSL certificate.
- `docker-compose.yml`: Docker Compose file to define and run multi-container Docker applications.

## Getting Started

To set up and run the project, follow these steps:

1. **Clone the Repository**

   ```sh
   git clone https://github.com/agentlans/https_flask_app.git
   cd https_flask_app
   ```

2. **Build and Run Containers**

   ```sh
   docker compose up --build
   ```

   This command builds the Docker images and starts the containers. The Flask app will be available at `https://localhost`.

## Customizing the Flask Application

To customize the Flask application:

1. **Edit `app.py`**

   Modify `app.py` to add new routes, change existing ones, or add more functionality to your Flask app.

2. **Add Dependencies**

   If you need additional Python libraries, add them to `requirements.txt` and rebuild the Docker images:

   ```sh
   docker compose build
   ```

## Customizing the Nginx Configuration

To change the Nginx settings:

1. **Edit `nginx/default.conf`**

   Adjust the Nginx configuration as needed. For example, you can add custom headers, change proxy settings, or configure additional locations.

2. **Rebuild the Nginx Docker Image**

   After modifying `default.conf`, rebuild the Nginx Docker image:

   ```sh
   docker compose build nginx
   ```

## Customizing Docker and Docker Compose

To customize the Docker setup:

1. **Modify `Dockerfile`**

   - **For Flask App**: Adjust the `Dockerfile` in the root directory if you need to change the base image, add additional setup steps, or modify the default command.

   - **For Nginx**: Edit the `nginx/Dockerfile` if you need a different base image or additional setup steps.

2. **Update `docker-compose.yml`**

   Modify `docker-compose.yml` to:
   - Change service names.
   - Adjust port mappings.
   - Add new services or remove existing ones.
   - Define environment variables.

   After making changes, run:

   ```sh
   docker compose up --build
   ```

   to apply the new configuration.

## Cleaning Up

To remove orphan containers (containers that are no longer associated with any service in the current `docker-compose.yml`):

```sh
docker compose up --build --remove-orphans
```

To stop and remove all containers and networks defined in `docker-compose.yml`:

```sh
docker compose down
```

## Troubleshooting

- **Logs**: Check logs for issues with:

  ```sh
  docker compose logs
  ```

- **Container Status**: Check the status of running containers with:

  ```sh
  docker ps
  ```

- **Container Logs**: Check individual container logs for more details:

  ```sh
  docker logs <container_name>
  ```

## Contributing

Feel free to fork the repository and submit pull requests. For major changes, please open an issue first to discuss what you would like to change.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.