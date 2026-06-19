FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY mondaycom/data-guard /app/provider/mondaycom/data-guard
WORKDIR /app/provider/mondaycom/data-guard
EXPOSE 6330
ENV PORT=6330
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6330/health || exit 1
CMD ["node", "index.js"]
