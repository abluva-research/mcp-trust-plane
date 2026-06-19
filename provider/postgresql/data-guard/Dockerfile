FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY postgresql/data-guard /app/provider/postgresql/data-guard
WORKDIR /app/provider/postgresql/data-guard
EXPOSE 6341
ENV PORT=6341
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6341/health || exit 1
CMD ["node", "index.js"]
