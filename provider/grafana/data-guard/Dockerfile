FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY grafana/data-guard /app/provider/grafana/data-guard
WORKDIR /app/provider/grafana/data-guard
EXPOSE 6325
ENV PORT=6325
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6325/health || exit 1
CMD ["node", "index.js"]
