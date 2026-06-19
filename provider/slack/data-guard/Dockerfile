FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY slack/data-guard /app/provider/slack/data-guard
WORKDIR /app/provider/slack/data-guard
EXPOSE 6345
ENV PORT=6345
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6345/health || exit 1
CMD ["node", "index.js"]
