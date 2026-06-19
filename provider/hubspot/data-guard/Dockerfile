FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY hubspot/data-guard /app/provider/hubspot/data-guard
WORKDIR /app/provider/hubspot/data-guard
EXPOSE 6326
ENV PORT=6326
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6326/health || exit 1
CMD ["node", "index.js"]
