
FROM node:18-alpine AS builder
WORKDIR /app
COPY services/moods-service/package*.json ./
RUN npm ci || npm install
COPY services/moods-service/ .
COPY ./protos ./protos

FROM node:18-alpine

WORKDIR /app
COPY --from=builder /app .
ENV NODE_ENV=production
ENV HOST=0.0.0.0
ENV PORT=50052
EXPOSE 50052

CMD ["node", "index.js"]