FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY wordpress/data-guard /app/provider/wordpress/data-guard
WORKDIR /app/provider/wordpress/data-guard
EXPOSE 6353
ENV PORT=6353
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6353/health || exit 1
CMD ["node", "index.js"]
