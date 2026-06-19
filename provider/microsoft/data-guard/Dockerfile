FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY microsoft/data-guard /app/provider/microsoft/data-guard
WORKDIR /app/provider/microsoft/data-guard
EXPOSE 6329
ENV PORT=6329
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6329/health || exit 1
CMD ["node", "index.js"]
