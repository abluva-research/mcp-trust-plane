FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY outlook/data-guard /app/provider/outlook/data-guard
WORKDIR /app/provider/outlook/data-guard
EXPOSE 6337
ENV PORT=6337
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6337/health || exit 1
CMD ["node", "index.js"]
