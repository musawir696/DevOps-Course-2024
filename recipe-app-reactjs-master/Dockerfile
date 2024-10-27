# Use the official Node.js image as the base
FROM node:14-alpine

# Set the working directory
WORKDIR /app

# Copy package.json and yarn.lock files to install dependencies
COPY package.json yarn.lock ./

# Install dependencies
RUN yarn install

# Copy the rest of the app’s code
COPY . .

# Build the app
RUN yarn build

# Use a lightweight web server to serve the build
FROM nginx:alpine
COPY --from=0 /app/build /usr/share/nginx/html

# Expose port 80 to access the app
EXPOSE 80

# Start the server
CMD ["nginx", "-g", "daemon off;"]
