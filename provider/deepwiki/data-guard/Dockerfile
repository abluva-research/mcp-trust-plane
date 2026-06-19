FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY deepwiki/data-guard /app/provider/deepwiki/data-guard
WORKDIR /app/provider/deepwiki/data-guard
EXPOSE 6314
ENV PORT=6314
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6314/health || exit 1
CMD ["node", "index.js"]
