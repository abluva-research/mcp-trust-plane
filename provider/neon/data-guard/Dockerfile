FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY neon/data-guard /app/provider/neon/data-guard
WORKDIR /app/provider/neon/data-guard
EXPOSE 6334
ENV PORT=6334
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6334/health || exit 1
CMD ["node", "index.js"]
