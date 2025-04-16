# Step 1: Use Node.js image to build the React app
FROM node:18 AS build

# Step 2: Set the working directory inside the container
WORKDIR /app

# Step 3: Copy package.json and package-lock.json to install dependencies
COPY package*.json ./

# Step 4: Install dependencies
RUN npm install

# Step 5: Copy the rest of the application code
COPY . .

# Step 6: Build the React app for production
RUN npm run build

# Step 7: Use Nginx to serve the built React app
FROM nginx:alpine

# Step 8: Copy the build files from the first stage to Nginx's default folder
COPY --from=build /app/build /usr/share/nginx/html

# Step 9: Expose port 80 for Nginx to serve the app
EXPOSE 80

# Step 10: Run Nginx to serve the app
CMD ["nginx", "-g", "daemon off;"]

