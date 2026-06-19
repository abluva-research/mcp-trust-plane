FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY azure/data-guard /app/provider/azure/data-guard
WORKDIR /app/provider/azure/data-guard
EXPOSE 6306
ENV PORT=6306
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6306/health || exit 1
CMD ["node", "index.js"]
