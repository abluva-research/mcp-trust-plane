FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY asana/data-guard /app/provider/asana/data-guard
WORKDIR /app/provider/asana/data-guard
EXPOSE 6302
ENV PORT=6302
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6302/health || exit 1
CMD ["node", "index.js"]
