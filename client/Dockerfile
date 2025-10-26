# Build stage
FROM node:18-alpine AS builder
WORKDIR /usr/src/app

COPY client/package*.json ./
RUN npm install
COPY client/ .
RUN npm run build

# Production stage: serve with nginx
FROM nginx:stable-alpine
COPY --from=builder /usr/src/app/build /usr/share/nginx/html

# Copy custom nginx.conf if needed (for routing / fallback)
# COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]