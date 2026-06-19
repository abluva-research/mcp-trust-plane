FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY cloudflare/data-guard /app/provider/cloudflare/data-guard
WORKDIR /app/provider/cloudflare/data-guard
EXPOSE 6311
ENV PORT=6311
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6311/health || exit 1
CMD ["node", "index.js"]
