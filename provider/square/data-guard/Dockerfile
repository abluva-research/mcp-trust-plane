FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY square/data-guard /app/provider/square/data-guard
WORKDIR /app/provider/square/data-guard
EXPOSE 6347
ENV PORT=6347
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6347/health || exit 1
CMD ["node", "index.js"]
