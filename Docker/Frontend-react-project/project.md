1. ```npm install``` to install dependencies. 
2. ```npm run test``` to run a test on the app.
3. ```npm run build``` to take all files and compact them into a single file called 'build'.
4. ```ls``` to see there's now a build directory.
5. ```ls build``` to look inside the build folder and see there is now an 'index.html' file and a 'static' file.
6. ```ls build/static``` to look inside static folder and see the 'js' (javascript) file with the application.
7. ```npm run start``` to automatically open a tab in web browser on localhost:3000 running the react app.
8. Create 'Dockerfile.dev' file in 'frontend' directory and the 'dev' tells docker this file is for the dev environment as normal 'Dockerfile' is for the prod environment.
9. ```docker build -f Dockerfile.dev -t image-name:tag .``` to build the docker file and create an image.
10. ```docker run -it -p 3000:3000 -v /app/node_modules -v $(pwd):/app image-name:tag``` to run the image you have just created and '-v /app/node_modules' creates an anonymous volume at '-v /app/node_modules' to prevent it from being overwritten by the next mount. The '-v $(pwd):/app' Mounts the current working directory on the host '($(pwd))' to '/app' inside the container instead of copying the whole folder which takes longer and isn't needed.
11. To run the image and run a test you would use the command ```docker run -it [image-name] npm run test ``` in a separate bash terminal, this creates a docker container for testing '-it' so you can interact and press enter to run tests.
12. The other way is creating a docker-compose file where you would build the container with the app the same as the dockerfile, but you would also add the test(s). ```docker-compose up --build``` to run the yml script, two containers are made, one for the app, the other for testing.
13. You can go into src/App.test.js file make changes and add tests, and the container with run the added tests immediately after you have saved.
14. This approach means I don't need to use another bash terminal to run the tests on the active container. I also don't need to get the container id and add it to the run command. The problem is you can't use the test suite with the keyboard shortcuts as could in the above option.


