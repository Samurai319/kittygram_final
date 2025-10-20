FROM node:18
WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

RUN npm ci

COPY . .
RUN npm run build
RUN mkdir -p /static && cp -r build/* /static/
RUN npm install --global http-server

CMD ["sh", "-c", "mkdir -p /static && cp -r /app/build/* /static/ && exec npx -y http-server -p 8000 /static"]
