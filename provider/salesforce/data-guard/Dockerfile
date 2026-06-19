FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY salesforce/data-guard /app/provider/salesforce/data-guard
WORKDIR /app/provider/salesforce/data-guard
EXPOSE 6344
ENV PORT=6344
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6344/health || exit 1
CMD ["node", "index.js"]
