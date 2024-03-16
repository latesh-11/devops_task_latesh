### Running the Application without Docker Image:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/latesh-11/Task_Latesh_Infa45Media.git
   cd Task_Latesh_Infa45Media/Next_js_Application/
   ```

2. **Install Node.js and npm:**
   Make sure you have Node.js and npm installed on your machine. You can download them from the [official website](https://nodejs.org/), or install them using a package manager.

3. **Install Dependencies:**
   ```bash
   npm install
   ```

4. **Set Environment Variables:**
   Replace `your-firebase-api-key`, `your-firebase-project-id`, and `your-firebase-app-id` with your actual Firebase credentials.
   ```bash
   export NEXT_PUBLIC_FIREBASE_API_KEY=your-firebase-api-key
   export NEXT_PUBLIC_FIREBASE_PROJECT_ID=your-firebase-project-id
   export NEXT_PUBLIC_FIREBASE_APP_ID=your-firebase-app-id
   ```

5. **Build the Application:**
   ```bash
   npm run build
   ```

6. **Run the Application:**
   ```bash
   npm start
   ```

7. **Access the Application:**
   Once the application is running, you can access it by navigating to `http://localhost:3000` in your web browser.

### Running the Application with Docker Image:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/latesh-11/Task_Latesh_Infa45Media.git
   cd Task_Latesh_Infa45Media/Next_js_Application/
   ```

2. **Build the Docker Image:**
   ```bash
   docker build -t nextjs-app .
   ```

3. **Run the Docker Container:**
   ```bash
   docker run -d -p 3000:3000 nextjs-app
   ```

4. **Access the Application:**
   Once the container is running, you can access the application by navigating to `http://localhost:3000` in your web browser.

### Stopping the Application or Container:

- **Without Docker:**
  Simply terminate the process running the application (usually by pressing `Ctrl + C`).

- **With Docker:**
  You can stop the Docker container using the following command:
  ```bash
  docker stop <container_id_or_name>
  ```
