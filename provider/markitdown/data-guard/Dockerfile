FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY markitdown/data-guard /app/provider/markitdown/data-guard
WORKDIR /app/provider/markitdown/data-guard
EXPOSE 6328
ENV PORT=6328
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6328/health || exit 1
CMD ["node", "index.js"]
