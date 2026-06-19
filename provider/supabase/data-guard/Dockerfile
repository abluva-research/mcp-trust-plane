FROM node:26-alpine
WORKDIR /app
COPY _lib /app/provider/_lib
COPY supabase/data-guard /app/provider/supabase/data-guard
WORKDIR /app/provider/supabase/data-guard
EXPOSE 6349
ENV PORT=6349
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:6349/health || exit 1
CMD ["node", "index.js"]
