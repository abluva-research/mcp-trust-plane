FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY duckduckgo/data-guard /app/provider/duckduckgo/data-guard
WORKDIR /app/provider/duckduckgo/data-guard
EXPOSE 6316
ENV PORT=6316
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6316/health || exit 1
CMD ["node", "index.js"]
