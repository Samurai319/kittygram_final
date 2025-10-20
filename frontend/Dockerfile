FROM node:18
WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

RUN npm ci

COPY . .
RUN npm run build

# Копируем вложенную папку static (где лежат js/css/media) прямо в корень /static/
RUN mkdir -p /static && cp -r build/static/* /static/
RUN cp -r build/* /static/ || true

RUN npm install --global http-server

CMD ["sh", "-c", "mkdir -p /static && cp -r /app/build/static/* /static/ && exec npx -y http-server -p 8000 /static"]
