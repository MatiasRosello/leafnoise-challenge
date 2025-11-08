# Etapa 1: Build de Angular
FROM node:20.19 AS build
WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build --prod

# Etapa 2: Servir con nginx
FROM nginx:stable-alpine

#Pisamos la configuración por defecto de nginx con la de nuestra build
COPY --from=build /app/dist/angular-conduit/browser/ /usr/share/nginx/html/

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
