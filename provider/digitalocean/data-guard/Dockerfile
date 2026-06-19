FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY digitalocean/data-guard /app/provider/digitalocean/data-guard
WORKDIR /app/provider/digitalocean/data-guard
EXPOSE 6315
ENV PORT=6315
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6315/health || exit 1
CMD ["node", "index.js"]
