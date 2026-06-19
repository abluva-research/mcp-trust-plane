FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY confluence/data-guard /app/provider/confluence/data-guard
WORKDIR /app/provider/confluence/data-guard
EXPOSE 6304
ENV PORT=6304
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6304/health || exit 1
CMD ["node", "index.js"]
