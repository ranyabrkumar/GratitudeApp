FROM node:18-alpine AS builder
WORKDIR /app
COPY services/stats-api/package*.json ./
RUN npm ci || npm install
COPY services/stats-api/ .
COPY ./protos ./protos

FROM node:18-alpine

WORKDIR /app
COPY --from=builder /app .
ENV NODE_ENV=production
ENV HOST=0.0.0.0
ENV PORT=5003
EXPOSE 5003

CMD ["node", "index.js"]