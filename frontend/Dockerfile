FROM node:18
WORKDIR /app

#копируются файлы с перечнем зависимостей проекта
COPY package.json package.json
COPY package-lock.json package-lock.json
# установка необходимых пакетов
RUN npm install

#исходный код приложения копируется в образ
COPY . .
#выполняется сборка приложения для публикации на сервере
# В образе в папке app/build/ будут сохранены
# файлы статики (HTML, JS и CSS) фронтенд-приложения.
RUN npm run build

# Эта команда запустит встроенный сервер на Node.js, который будет раздавать
# содержимое директории /app/build на порте 8000 прямо из контейнера
CMD ["npx", "-y", "http-server", "-p", "8000", "/app/build"] 
