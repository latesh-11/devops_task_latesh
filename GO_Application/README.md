### Running the Application without Docker Image:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/latesh-11/Task_Latesh_Infa45Media.git
   cd Task_Latesh_Infa45Media
   ```

2. **Install Go:**
   Make sure you have Go installed on your machine. You can download it from the [official website](https://golang.org/dl/), or install it using a package manager.

3. **Build the Application:**
   ```bash
   go build -o helloserver ./helloserver/server.go
   ```

4. **Run the Application:**
   ```bash
   ./helloserver
   ```

5. **Access the Application:**
   Once the application is running, you can access it by navigating to `http://localhost:8080` in your web browser.

### Running the Application with Docker Image:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/latesh-11/Task_Latesh_Infa45Media.git
   cd Task_Latesh_Infa45Media
   ```

2. **Build the Docker Image:**
   ```bash
   docker build -t helloserver .
   ```

3. **Run the Docker Container:**
   ```bash
   docker run -d -p 8080:8080 helloserver
   ```

4. **Access the Application:**
   Once the container is running, you can access the application by navigating to `http://localhost:8080` in your web browser.

### Stopping the Application or Container:

- **Without Docker:**
  Simply terminate the process running the application (usually by pressing `Ctrl + C`).

- **With Docker:**
  You can stop the Docker container using the following command:
  ```bash
  docker stop <container_id_or_name>
  ```

