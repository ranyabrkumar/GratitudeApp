
FROM node:18-alpine AS builder
WORKDIR /app
COPY services/moods-api/package*.json ./
RUN npm ci || npm install
COPY services/moods-api/ .
COPY ./protos ./protos

FROM node:18-alpine

WORKDIR /app
COPY --from=builder /app .
ENV NODE_ENV=production
ENV HOST=0.0.0.0
ENV PORT=5002
EXPOSE 5002

CMD ["node", "index.js"]