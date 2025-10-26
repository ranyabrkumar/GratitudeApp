FROM node:18-alpine AS builder
WORKDIR /app
COPY services/stats-service/package*.json ./
RUN npm ci || npm install
COPY services/stats-service/ .
COPY ./protos ./protos

FROM node:18-alpine

WORKDIR /app
COPY --from=builder /app .
ENV NODE_ENV=production
ENV HOST=0.0.0.0
ENV PORT=50053
EXPOSE 50053

CMD ["node", "index.js"]