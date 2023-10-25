# Stage 1: Build the Angular application
FROM node:21 AS build
WORKDIR /usr/src/app
COPY package*.json ./
RUN yarn install
COPY . .
RUN yarn run build


# Stage 2: Serve the application from nginx
FROM nginx:alpine
COPY --from=build /usr/src/app/dist/ /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
