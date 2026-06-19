FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY atlassian/data-guard /app/provider/atlassian/data-guard
WORKDIR /app/provider/atlassian/data-guard
EXPOSE 6303
ENV PORT=6303
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6303/health || exit 1
CMD ["node", "index.js"]
