FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY datadog/data-guard /app/provider/datadog/data-guard
WORKDIR /app/provider/datadog/data-guard
EXPOSE 6313
ENV PORT=6313
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6313/health || exit 1
CMD ["node", "index.js"]
