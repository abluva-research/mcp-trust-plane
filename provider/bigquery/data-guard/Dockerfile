FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY bigquery/data-guard /app/provider/bigquery/data-guard
WORKDIR /app/provider/bigquery/data-guard
EXPOSE 6307
ENV PORT=6307
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6307/health || exit 1
CMD ["node", "index.js"]
