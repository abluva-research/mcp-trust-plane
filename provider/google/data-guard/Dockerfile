FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY google/data-guard /app/provider/google/data-guard
WORKDIR /app/provider/google/data-guard
EXPOSE 6324
ENV PORT=6324
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6324/health || exit 1
CMD ["node", "index.js"]
