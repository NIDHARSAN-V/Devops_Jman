FROM  node:18-alpine AS react_builder
WORKDIR /app
COPY package.json ./
COPY package-lock.json ./
RUN npm ci
COPY . .
RUN npm run build

# ------------------------------------------------------------------------------------------------------------------------------------

FROM nginx:alpine
COPY --from=react_builder /app/dist  /usr/share/nginx/html
EXPOSE 80
# CMD []
CMD ["nginx" , "-g" ,"daemon off;"]


# CMD ["sh", "-c", "cp /var/log/nginx/access.log /usr/share/nginx/html/access.log 2>/dev/null || true; exec nginx -g 'daemon off;'"]