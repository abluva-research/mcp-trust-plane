FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY mongodb/data-guard /app/provider/mongodb/data-guard
WORKDIR /app/provider/mongodb/data-guard
EXPOSE 6331
ENV PORT=6331
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6331/health || exit 1
CMD ["node", "index.js"]
