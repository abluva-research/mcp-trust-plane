FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY pagerduty/data-guard /app/provider/pagerduty/data-guard
WORKDIR /app/provider/pagerduty/data-guard
EXPOSE 6338
ENV PORT=6338
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6338/health || exit 1
CMD ["node", "index.js"]
