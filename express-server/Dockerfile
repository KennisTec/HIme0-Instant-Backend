# Stage 1: Build the app
FROM node:18 AS build

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm install

COPY . .

# Build the app (optional, if you want to use a production build)
RUN npm run build

# Stage 2: Run the app
FROM node:18-slim

WORKDIR /app

COPY --from=build /app /app

EXPOSE 3000

CMD ["npm", "run", "start"]