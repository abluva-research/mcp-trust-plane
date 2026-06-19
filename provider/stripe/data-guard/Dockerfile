FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY stripe/data-guard /app/provider/stripe/data-guard
WORKDIR /app/provider/stripe/data-guard
EXPOSE 6348
ENV PORT=6348
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6348/health || exit 1
CMD ["node", "index.js"]
