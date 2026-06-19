FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY mysql/data-guard /app/provider/mysql/data-guard
WORKDIR /app/provider/mysql/data-guard
EXPOSE 6333
ENV PORT=6333
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6333/health || exit 1
CMD ["node", "index.js"]
