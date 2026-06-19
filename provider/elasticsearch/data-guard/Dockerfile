FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY elasticsearch/data-guard /app/provider/elasticsearch/data-guard
WORKDIR /app/provider/elasticsearch/data-guard
EXPOSE 6318
ENV PORT=6318
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6318/health || exit 1
CMD ["node", "index.js"]
