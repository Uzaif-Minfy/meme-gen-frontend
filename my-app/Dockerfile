FROM node:18 AS builder

WORKDIR /app
COPY . .

RUN npm install tailwindcss @tailwindcss/vite \
    && npm install dotenv \
    && npm install firebase react-router-dom \
    && npm install @reduxjs/toolkit react-redux \
    && npm install react@18 react-dom@18 react-draggable \
    && npm install dom-to-image-more \
    && npm install

COPY .env ./

RUN npm run build

FROM nginx:stable-alpine

COPY --from=builder /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
