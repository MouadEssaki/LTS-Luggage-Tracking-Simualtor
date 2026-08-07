# ── Stage 1 : Build (Compile Angular) ─────────────────────────────────
FROM node:20-alpine AS build
WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build -- --configuration=production

# ── Stage 2 : Serve (Utilise Nginx pour servir les fichiers) ──────────
FROM nginx:alpine

# Copie les fichiers buildés vers le dossier de Nginx
COPY --from=build /app/dist/LTS-frontend/browser /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]