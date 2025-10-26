FROM node:18-alpine AS builder
WORKDIR /app
COPY services/server-main/package*.json ./
RUN npm ci || npm install
COPY services/server-main/ .
COPY ./protos ./protos

FROM node:18-alpine

WORKDIR /app
COPY --from=builder /app .
ENV NODE_ENV=production
ENV HOST=0.0.0.0
ENV PORT=5001
EXPOSE 5001

CMD ["node", "index.js"]