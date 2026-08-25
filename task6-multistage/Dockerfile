FROM node:20-alpine AS builder

WORKDIR /app

COPY package.json .
COPY index.html .

RUN npm run build

FROM nginx:alpine

COPY --from=builder /app/dist/index.html /usr/share/nginx/html/index.html