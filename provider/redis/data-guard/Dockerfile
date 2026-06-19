FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY redis/data-guard /app/provider/redis/data-guard
WORKDIR /app/provider/redis/data-guard
EXPOSE 6343
ENV PORT=6343
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6343/health || exit 1
CMD ["node", "index.js"]
