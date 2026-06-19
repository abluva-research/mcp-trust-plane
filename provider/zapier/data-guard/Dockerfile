FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY zapier/data-guard /app/provider/zapier/data-guard
WORKDIR /app/provider/zapier/data-guard
EXPOSE 6354
ENV PORT=6354
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6354/health || exit 1
CMD ["node", "index.js"]
