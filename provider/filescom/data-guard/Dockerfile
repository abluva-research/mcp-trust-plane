FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY filescom/data-guard /app/provider/filescom/data-guard
WORKDIR /app/provider/filescom/data-guard
EXPOSE 6320
ENV PORT=6320
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6320/health || exit 1
CMD ["node", "index.js"]
