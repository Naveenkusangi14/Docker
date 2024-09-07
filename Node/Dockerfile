# Stage 1: Build Stage
FROM node AS build

# Set working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files (main.js)
COPY main.js ./

# Stage 2: Production Stage
FROM gcr.io/distroless/nodejs18-debian12

# Set working directory in the production container
WORKDIR /app

# Copy the build artifacts from the build stage
COPY --from=build /app /app

# Run the application
CMD ["main.js"]
