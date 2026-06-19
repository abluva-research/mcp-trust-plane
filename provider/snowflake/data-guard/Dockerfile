FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY snowflake/data-guard /app/provider/snowflake/data-guard
WORKDIR /app/provider/snowflake/data-guard
EXPOSE 6346
ENV PORT=6346
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6346/health || exit 1
CMD ["node", "index.js"]
