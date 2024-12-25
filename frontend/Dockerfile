# Stage 1: Build the Frontend
FROM node:21 AS frontend-builder

WORKDIR /app

COPY package*.json ./

RUN npm install newrelic --save

ENV NEW_RELIC_NO_CONFIG_FILE=true


COPY . .

# Stage 2: Create the final image
FROM node:21-slim

WORKDIR /app

COPY --from=frontend-builder /app .

COPY .env.sample .env.local

EXPOSE 8080

CMD ["npm", "run" , "dev" , "--" , "--host"]
