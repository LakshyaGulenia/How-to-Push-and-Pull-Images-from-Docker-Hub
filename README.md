
# How to Push and Pull Images from Docker Hub

### Step 1: Create a Docker Hub Account
Before pushing an image to Docker Hub, you need to create an account on [Docker Hub](https://hub.docker.com/).

### Step 2: Create a Container on Your EC2 Ubuntu Machine
Run the following command to create a container:
```bash
docker run -it ubuntu /bin/bash
```
- If the Ubuntu image is not available locally, Docker will download it from Docker Hub.
- Once the container is running, you will be inside the container.

### Step 3: Create Files for Testing
Inside the container, you can create files to test the setup:
1. To view the files in the current directory:
   ```bash
   ls
   ```
2. To create files named `file1`, `file2`, `test1`, and `test2`:
   ```bash
   touch file1 file2 test1 test2
   ```
3. To verify that the files were created:
   ```bash
   ls
   ```

### Step 4: Create Files in the `/tmp` Directory
Navigate to the `/tmp` folder:
```bash
cd /tmp
```
Create files for testing:
```bash
touch file5 file6
```
Verify the files:
```bash
ls
```

### Step 5: Exit the Container
Type `exit` to leave the container.

### Step 6: Create an Image from the Container
To create an image from the container, run the following command:
```bash
docker commit <container_name> <new_image_name>
```
Replace `<container_name>` with your container's name and `<new_image_name>` with the desired image name.

To verify that the image was created, type:
```bash
docker images
```

### Step 7: Log In to Docker Hub
Log in to your Docker Hub account:
```bash
docker login
```
Enter your Docker Hub username and password when prompted. If successful, it will display:
```
Login Succeeded
```

### Step 8: Tag the Image
Tag your image before pushing it to Docker Hub:
```bash
docker tag <image_name> <dockerhub_username>/<new_image_name>
```
Replace `<image_name>` with the name of your local image and `<dockerhub_username>` with your Docker Hub username.

### Step 9: Push the Image to Docker Hub
Push the tagged image to Docker Hub:
```bash
docker push <dockerhub_username>/<new_image_name>
```

You can check Docker Hub to verify that the image was successfully uploaded.

### Step 10: Pull the Image from Docker Hub on Another EC2 Machine
On another EC2 machine, you can pull the image from Docker Hub:
```bash
docker pull <dockerhub_username>/<image_name>
```

### Step 11: Create a Container from the Pulled Image
Create a container from the pulled image:
```bash
docker run -it --name <container_name> <image_name> /bin/bash
```
Replace `<container_name>` with the name you want to give the container and `<image_name>` with the name of the image you pulled.
