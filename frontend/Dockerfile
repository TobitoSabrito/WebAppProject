# Stage 1: Build the React application
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 2: Serve the application with a lightweight server
FROM node:20-alpine
WORKDIR /app
COPY --from=build /app/dist /app/dist

# Install a simple static server
RUN npm install -g serve

# Expose port 3000
EXPOSE 3000

# Command to run the server
CMD ["serve", "-s", "dist", "-l", "3000"] 