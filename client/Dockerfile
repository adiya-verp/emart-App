FROM node:14 AS web_build
WORKDIR  /usr/src/app
COPY ./ ./client
RUN cd client && npm install && npm run build --prod

# Use official image as base image
FROM nginx:latest

# Copy the artifact and replace into nginx default content
COPY --from=web_build /usr/src/app/client/dist/client/ /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 4200