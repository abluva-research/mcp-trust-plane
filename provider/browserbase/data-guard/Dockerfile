FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY browserbase/data-guard /app/provider/browserbase/data-guard
WORKDIR /app/provider/browserbase/data-guard
EXPOSE 6309
ENV PORT=6309
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6309/health || exit 1
CMD ["node", "index.js"]
