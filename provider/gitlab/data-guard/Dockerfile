FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY gitlab/data-guard /app/provider/gitlab/data-guard
WORKDIR /app/provider/gitlab/data-guard
EXPOSE 6322
ENV PORT=6322
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6322/health || exit 1
CMD ["node", "index.js"]
