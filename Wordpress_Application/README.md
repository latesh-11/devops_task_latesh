To run the WordPress application using Docker, you can follow these steps:

1. **Create a Dockerfile:**
   Create a file named `Dockerfile` and paste the following content:

   ```Dockerfile
   FROM wordpress:latest
   
   WORKDIR /var/www/html
   
   COPY . /var/www/html
   
   EXPOSE 80
   
   ENV WORDPRESS_DB_HOST db
   ENV WORDPRESS_DB_USER wordpress
   ENV WORDPRESS_DB_PASSWORD wordpress
   ENV WORDPRESS_DB_NAME wordpress
   
   CMD ["apache2-foreground"]
   ```

   This Dockerfile sets up a WordPress container, copies the WordPress files into the container, exposes port 80, and sets up environment variables for the WordPress database connection.

2. **Build the Docker Image:**
   Run the following command in the directory containing your Dockerfile to build the Docker image:

   ```bash
   docker build -t my-wordpress .
   ```

   Replace `my-wordpress` with your desired image name.

3. **Run the Docker Container:**
   Now, you can run the Docker container using the following command:

   ```bash
   docker run -d -p 8080:80 --name my-wordpress-container my-wordpress
   ```

   This command will start a container named `my-wordpress-container` based on the `my-wordpress` image, and it will map port 8080 on your local machine to port 80 inside the container. Adjust the port mapping (`-p`) if needed.

4. **Access WordPress:**
   Once the container is running, you can access WordPress by navigating to `http://localhost:8080` in your web browser.

5. **Stop the Container (Optional):**
   If you want to stop the container, you can use the following command:

   ```bash
   docker stop my-wordpress-container
   ```

   Replace `my-wordpress-container` with the name of your running container.
