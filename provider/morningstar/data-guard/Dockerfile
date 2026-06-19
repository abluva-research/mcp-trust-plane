FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY morningstar/data-guard /app/provider/morningstar/data-guard
WORKDIR /app/provider/morningstar/data-guard
EXPOSE 6332
ENV PORT=6332
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6332/health || exit 1
CMD ["node", "index.js"]
