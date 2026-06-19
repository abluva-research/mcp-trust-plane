FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY terraform/data-guard /app/provider/terraform/data-guard
WORKDIR /app/provider/terraform/data-guard
EXPOSE 6352
ENV PORT=6352
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6352/health || exit 1
CMD ["node", "index.js"]
