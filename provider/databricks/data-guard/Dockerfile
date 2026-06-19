FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY databricks/data-guard /app/provider/databricks/data-guard
WORKDIR /app/provider/databricks/data-guard
EXPOSE 6312
ENV PORT=6312
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6312/health || exit 1
CMD ["node", "index.js"]
