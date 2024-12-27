# Базовый образ
FROM node:18-alpine

# Рабочая директория
WORKDIR /app

# Копируем package.json и package-lock.json
COPY package*.json ./

# Устанавливаем зависимости
RUN npm install

# Копируем исходный код приложения
COPY . .

# Сборка приложения
RUN npm run build

# Устанавливаем nginx
FROM nginx:alpine

# Копируем собранные файлы Vite в nginx
COPY --from=0 /app/dist /usr/share/nginx/html

# Запуск nginx
CMD ["nginx", "-g", "daemon off;"]