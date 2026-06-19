FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY github/data-guard /app/provider/github/data-guard
WORKDIR /app/provider/github/data-guard
EXPOSE 6305
ENV PORT=6305
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6305/health || exit 1
CMD ["node", "index.js"]
