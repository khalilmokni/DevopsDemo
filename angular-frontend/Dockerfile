# Stage 1: Build Angular app
FROM node:14.17.0-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Serve Angular app with nginx
FROM nginx:1.21.0-alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist/angular-frontend /usr/share/nginx/html
EXPOSE 80
