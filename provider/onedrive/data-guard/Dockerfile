FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY onedrive/data-guard /app/provider/onedrive/data-guard
WORKDIR /app/provider/onedrive/data-guard
EXPOSE 6336
ENV PORT=6336
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6336/health || exit 1
CMD ["node", "index.js"]
