---
title: "Создание проекта с использованием Webpack"
date: 2026-04-22
draft: false
---

---
# Лабораторная работа: Создание проекта с использованием Webpack
---

## 1. Установка и подготовка проекта

Сначала создала новый проект и установила необходимые зависимости.

```bash
mkdir webpack-lab
cd webpack-lab
npm init -y
npm i luxon
npm i -D webpack webpack-cli serve
mkdir src
touch src/index.js
open -e src/index.js
```

Открыла файл index.js и добавила туда код:   

```javascript
import { DateTime } from 'luxon';

setInterval(() => {
  document.getElementById('hh').textContent = DateTime
    .local()
    .setLocale('ru')
    .toFormat('dd.LL.yyyy HH:mm:ss');
}, 1000);
```
На данном шаге была сделана сборка проекта с помощью Webpack

```bash
npx webpack
```

НО у меня появилась ошибка:

```bash
Module parse failed: 'import' and 'export' may appear only with 'sourceType: module'
```

Я так поняла, что она связана с тем, что Webpack по умолчанию ожидает CommonJS, а в коде используется синтаксис ES-модулей (import).

Для устранения ошибки был настроен файл конфигурации webpack.config.js

```javascript
module.exports = {
  mode: 'development',
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: __dirname + '/dist'
  }
};
```

![Скриншот 1](https://github.com/vikisses/hugo_portfolio/blob/gh-pages/images/Webpack_1.png)

![Скриншот 2](https://github.com/vikisses/hugo_portfolio/blob/gh-pages/images/Webpack_2.png)

---

## 2. Создание страницы и подключение Bootstrap CDN

В корневой папке проекта был создан файл index.html:

```html
<!doctype html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Webpack + Luxon</title>

  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.7/dist/css/bootstrap.min.css"
    rel="stylesheet"
  />
</head>
<body class="bg-light">
  <div class="container py-5 text-center">
    <h1 class="display-4 mb-4">Текущее время</h1>
    <h1 id="hh" class="display-1 fw-bold text-primary"></h1>
  </div>

  <script src="./dist/main.js"></script>
</body>
</html>
```

Для корректного отображения использовался Bootstrap через CDN.
Время выводится крупно с помощью классов Bootstrap.

Внешний вид страницы после запуска:
![Скриншот 3](https://github.com/vikisses/hugo_portfolio/blob/gh-pages/images/Webpack_3.png)


---

## 3. Docker

Содержимое файла Dockerfile:

```dockerfile
FROM node:24-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npx webpack --mode development

EXPOSE 3000

CMD ["npx", "serve", ".", "-l", "3000"]
```

Последовательность действий для запуска в Docker:
Сначала выполняется сборка Docker-образа:

```bash
docker build -t webpack-lab .
```
Затем выполняется запуск контейнера:

```bash
docker run -p 3000:3000 webpack-lab
```

После запуска приложение становится доступно по адресу: http://localhost:3000/

![Скриншот 4](https://github.com/vikisses/hugo_portfolio/blob/gh-pages/images/Docker1.png)

Также в логах отображаются HTTP-запросы (GET / и GET /dist/main.js), что свидетельствует о корректной работе приложения внутри контейнера.

При обновлении страницы в браузере появляются новые записи в логах, что подтверждает обработку запросов сервером.

![Скриншот 5](https://github.com/vikisses/hugo_portfolio/blob/gh-pages/images/Docker2.png)


---
