FROM node:18-alpine3.17 as build_stage
WORKDIR /app
COPY . /app
RUN npm install
RUN npm run build
#Production stage
FROM ubuntu AS production_stage
RUN apt-get update
RUN apt-get install nginx -y
COPY --from=build_stage /app/dist /var/www/html/
EXPOSE 80
CMD ["nginx","-g","daemon off;"]