FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY notion/data-guard /app/provider/notion/data-guard
WORKDIR /app/provider/notion/data-guard
EXPOSE 6335
ENV PORT=6335
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6335/health || exit 1
CMD ["node", "index.js"]
