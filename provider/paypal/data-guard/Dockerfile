FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY paypal/data-guard /app/provider/paypal/data-guard
WORKDIR /app/provider/paypal/data-guard
EXPOSE 6339
ENV PORT=6339
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6339/health || exit 1
CMD ["node", "index.js"]
