# inherit from a existing image to add the functionality
FROM node

# Set the working directory and assign ownership to the non-root user
workdir /app

# Copy the package.json and package-lock.json files into the image.
COPY package*.json ./

# Install the dependencies.
RUN npm install 

# Copy the rest of the source files into the image.
COPY . .

# Expose the port that the application listens on.
EXPOSE 3000

# Run the application.
RUN npm run dev
