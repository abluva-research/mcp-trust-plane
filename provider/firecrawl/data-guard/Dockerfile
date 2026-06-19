FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY firecrawl/data-guard /app/provider/firecrawl/data-guard
WORKDIR /app/provider/firecrawl/data-guard
EXPOSE 6321
ENV PORT=6321
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6321/health || exit 1
CMD ["node", "index.js"]
