FROM node:24-alpine AS build-stage
WORKDIR /app

COPY react-board/package*.json ./
RUN npm install

COPY react-board/ ./
RUN npm run build

FROM nginx:alpine

RUN rm /etc/nginx/conf.d/default.conf
COPY nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=build-stage /app/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
 

