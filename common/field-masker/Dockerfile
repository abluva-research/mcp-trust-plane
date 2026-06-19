FROM node:26-alpine
WORKDIR /app
COPY package.json index.js ./
EXPOSE 6008
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6008/health || exit 1
CMD ["node", "index.js"]
