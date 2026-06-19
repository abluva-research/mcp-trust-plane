FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY brave-search/data-guard /app/provider/brave-search/data-guard
WORKDIR /app/provider/brave-search/data-guard
EXPOSE 6308
ENV PORT=6308
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6308/health || exit 1
CMD ["node", "index.js"]
