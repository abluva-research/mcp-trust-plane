FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY linear/data-guard /app/provider/linear/data-guard
WORKDIR /app/provider/linear/data-guard
EXPOSE 6327
ENV PORT=6327
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6327/health || exit 1
CMD ["node", "index.js"]
