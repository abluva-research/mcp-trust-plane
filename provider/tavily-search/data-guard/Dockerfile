FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY tavily-search/data-guard /app/provider/tavily-search/data-guard
WORKDIR /app/provider/tavily-search/data-guard
EXPOSE 6351
ENV PORT=6351
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6351/health || exit 1
CMD ["node", "index.js"]
