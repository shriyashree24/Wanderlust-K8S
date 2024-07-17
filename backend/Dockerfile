# Stage 1: Build the backend
FROM node:21 AS backend-builder

WORKDIR /app

COPY . .

RUN npm i

# Stage 2: Create the final image
FROM node:21-slim

WORKDIR /app

COPY --from=backend-builder /app .

COPY .env.docker .env

EXPOSE 5000

CMD ["npm", "start"]                         
