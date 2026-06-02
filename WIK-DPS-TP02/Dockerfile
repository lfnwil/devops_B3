FROM node:24-alpine

WORKDIR /app

COPY package*.json ./
COPY tsconfig.json server.ts ./

RUN npm ci \
    && npm run build \
    && npm prune --omit=dev

ENV NODE_ENV=production
ENV PORT=3000

EXPOSE 3000

CMD ["node", "dist/server.js"]
