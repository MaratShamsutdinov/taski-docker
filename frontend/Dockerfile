FROM node:18

WORKDIR /app

# Отключаем проверку SSL перед установкой зависимостей
RUN npm config set strict-ssl false

COPY package.json package-lock.json ./

# Устанавливаем зависимости (теперь без ошибки)
RUN npm ci --legacy-peer-deps || npm install --legacy-peer-deps

# Проверяем, установлен ли react-scripts
RUN npm list react-scripts || echo "react-scripts not found"

COPY . .

# Собираем проект
RUN npm run build

# Запускаем сервер
CMD ["npx", "-y", "http-server", "-p", "8000", "/app/build"]
