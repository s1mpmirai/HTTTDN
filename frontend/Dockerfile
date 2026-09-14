# ── Stage 1: Build React app ──────────────────────────────────
FROM node:20-alpine AS builder

WORKDIR /app

# Copy package files trước để tận dụng Docker cache
COPY package*.json ./
RUN npm install

# Copy source code và build
COPY . .
RUN npm run build

# ── Stage 2: Serve với Nginx ───────────────────────────────────
FROM nginx:alpine

# Copy build output sang nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Config nginx để hỗ trợ React Router (SPA)
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
