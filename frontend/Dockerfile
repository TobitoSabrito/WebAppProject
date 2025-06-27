# Stage 1: Build the React application
FROM node:20-alpine AS build
WORKDIR /app

# Sadece package.json'u kopyala
COPY package.json ./

# Linux ortamında lockfile oluştur
RUN npm install

# Uygulama kaynaklarını kopyala
COPY . .

# Build işlemi
RUN npm run build

# Stage 2: Serve the application with a lightweight server
FROM node:20-alpine
WORKDIR /app

# Sadece build çıktısını kopyala
COPY --from=build /app/dist /app/dist

# Static server kur
RUN npm install -g serve

EXPOSE 3000

CMD ["serve", "-s", "dist", "-l", "3000"] 