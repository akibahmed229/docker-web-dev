# this file is used to create a docker image for the react app and run it in a container using docker  & it will update the changes automatically
# docker build -t react-docker .
# docker run -p 5173:5173 -v "$(pwd):/app" -v '/app/node_modules' react-docker
# docker tag react-docker:latest <dockerhub_username>/react-docker:latest # to push the image to dockerhub

# set the base image to create the image from react app
FROM node:20-alpine

# create a new user with permissions to run the app
# if the app is run as root, it will be a security risk, in that case the app can be exploited to gain access to the host
RUN addgroup app && adduser  -S -G app app

# set the user to run the app
USER app

# set the working directory
WORKDIR /app


# copy package.json and package-lock.json to the working directory
# This is done before copying the rest of the files to take advantage of Docker’s cache
# If the package.json and package-lock.json files haven’t changed, Docker will use the cached dependencies
COPY package*.json ./

# sometimes the ownership of the files in the working directory is changed to root
# and thus the app can't access the files and throws an error -> EACCES: permission denied
# to avoid this, change the ownership of the files to the root user
USER root


# change the ownership of the /app directory to the app user
# chown -R <user>:<group> <directory>
# chown command changes the user and/or group ownership of for given file.
RUN chown -R app:app .

# change the user back to app
USER app

# install the dependencies
RUN yarn install

# copy the rest of the files to the working directory
COPY . .

# expose the port 5100 to tell Docker that the container listens on the specified network ports at runtime
EXPOSE 5173

# run the app
CMD yarn run dev
