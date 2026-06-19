FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY exa-search/data-guard /app/provider/exa-search/data-guard
WORKDIR /app/provider/exa-search/data-guard
EXPOSE 6319
ENV PORT=6319
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6319/health || exit 1
CMD ["node", "index.js"]
