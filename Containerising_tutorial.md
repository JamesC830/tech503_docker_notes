# Containerising tutorial

Example: [Dockerfile](https://github.com/JamesC830/tech503_docker_notes/blob/main/sparta_test_app/Dockerfile)

- Got the the repository where you have your app file
- Add a Dockerfile to that repo
- In the dockerfile you need to:
  - Use a base image from dockerhub
  - Define your working directory in the container
  - Copy over the files to the container
  - Install any dependancies
  - Expose the posrt you want to run on
  - Run your app
- The in the terminal you can:
  - Navigate to sparta test app folder with the dockerfile "C:\Users\jcunn\nodejs20-sparta-test-app\app"
  - ```docker build -t sparta-test-app .```
  - ```docker run -d -p 3000:3000 sparta-test-app```
- Open your browser and go to http://localhost:3000
- To stop the container: ```docker stop sparta-test-app```
- To delete the container (after stopping it): ```docker rm sparta-test-app```