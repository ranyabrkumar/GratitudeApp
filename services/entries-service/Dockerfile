
FROM node:18-alpine AS builder
WORKDIR /app
COPY services/entries-service/package*.json ./
RUN npm ci || npm install
COPY services/entries-service/ .
COPY ./protos ./protos

FROM node:18-alpine

WORKDIR /app
COPY --from=builder /app .
ENV NODE_ENV=production
ENV HOST=0.0.0.0
ENV PORT=50051
EXPOSE 50051

CMD ["node", "index.js"]
