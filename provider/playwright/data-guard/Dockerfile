FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY playwright/data-guard /app/provider/playwright/data-guard
WORKDIR /app/provider/playwright/data-guard
EXPOSE 6340
ENV PORT=6340
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6340/health || exit 1
CMD ["node", "index.js"]
