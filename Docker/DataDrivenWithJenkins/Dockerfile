# Use the official Node.js 16 image as the base image
FROM node:20

# Set the working directory in the container(linux)
WORKDIR /app


# Install Newman globally
RUN npm install -g newman

#Install Newman html report
RUN npm install -g newman-reporter-html

#Install Newman Reporter HTMLExtra
RUN npm install -g newman-reporter-htmlextra

#Ensure the result directory exists
RUN mkdir -p /app/result/


# Copy your Postman collection and environment files to the working directory
COPY DataDrivenAPIsCollection.json /app/
COPY GoRestEnv.json /app/
COPY myuser.csv /app/

# Set the command to run Newman and execute your Postman collection
CMD ["newman", "run", "/app/DataDrivenAPIsCollection.json", "-e", "/app/GoRestEnv.json", "-d", "/app/myuser.csv", "-r", "cli,json,html,htmlextra", "--reporter-htmlextra-export", "/app/results/gorest.html"]