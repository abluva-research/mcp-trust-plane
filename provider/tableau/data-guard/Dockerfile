FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY tableau/data-guard /app/provider/tableau/data-guard
WORKDIR /app/provider/tableau/data-guard
EXPOSE 6350
ENV PORT=6350
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6350/health || exit 1
CMD ["node", "index.js"]
