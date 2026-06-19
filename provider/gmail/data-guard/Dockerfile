FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY gmail/data-guard /app/provider/gmail/data-guard
WORKDIR /app/provider/gmail/data-guard
EXPOSE 6323
ENV PORT=6323
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6323/health || exit 1
CMD ["node", "index.js"]
