FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY postman/data-guard /app/provider/postman/data-guard
WORKDIR /app/provider/postman/data-guard
EXPOSE 6342
ENV PORT=6342
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6342/health || exit 1
CMD ["node", "index.js"]
