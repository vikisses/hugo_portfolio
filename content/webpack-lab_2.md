---
title: "Интеграция Bootstrap 5 в приложение с luxon. Этап 2"
date: 2026-05-15
draft: false
---

---
# Лабораторная работа: Интеграция Bootstrap 5 в приложение с luxon. Этап 2
---

## 1. Cкриншот с кодом html

Код html:

```html
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>Bootstrap + Luxon</title>

  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
    rel="stylesheet"
  >
</head>

<body>

  <div class="container mt-5">
    <div class="row">

      <div class="col-2"></div>

      <div class="col-8">
        <button
          class="btn btn-danger btn-lg w-100"
          data-bs-toggle="modal"
          data-bs-target="#timeModal"
        >
          Показать время
        </button>
      </div>

      <div class="col-2"></div>

    </div>
  </div>

  <div class="modal fade" id="timeModal" tabindex="-1">
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">

        <div class="modal-header">
          <h5 class="modal-title">
            Выполнила: Виктория Тарасова
          </h5>

          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
          ></button>
        </div>

        <div class="modal-body text-center">
          <h1 id="hh"></h1>
        </div>

        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
          >
            Закрыть
          </button>
        </div>

      </div>
    </div>
  </div>

  <script src="./dist/main.js"></script>

  <script
    src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js">
  </script>

</body>
</html>
```

![Код html](https://github.com/vikisses/hugo_portfolio/blob/gh-pages/images/web_2_htmlcode.png)

---

## 2. Внешний вид приложения с раскрытым окном


![Внешний вид приложения](https://github.com/vikisses/hugo_portfolio/blob/gh-pages/images/web_2_front_side.png)


---

## 3. Последовательность выполненных действий.

Была создана папка проекта и выполнена инициализация npm-проекта с помощью команды npm init -y. После этого была установлена библиотека Luxon командой npm i luxon, а также зависимости для сборки проекта: webpack, webpack-cli и serve.

Далее была создана папка src, внутри которой был создан файл index.js. В этот файл был добавлен код с импортом библиотеки Luxon и выводом текущей даты и времени.

После этого был создан файл index.html. В него была подключена библиотека Bootstrap 5 через CDN. С помощью Bootstrap была реализована структура страницы из трёх колонок в соотношении 2-8-2. В центральной колонке была размещена большая красная кнопка «Показать время».

Затем было добавлено модальное окно Bootstrap. В заголовке окна была указана моя фамилия и имя, а в основной части окна выводились текущие дата и время, полученные с помощью библиотеки Luxon. Также были реализованы два способа закрытия окна: с помощью крестика в правом верхнем углу и кнопки «Закрыть» в нижней части окна.

После завершения разработки была выполнена сборка проекта командой npx webpack, в результате чего был создан файл dist/main.js. Затем проект был запущен локально с помощью команды npx serve ., после чего приложение стало доступно в браузере по адресу http://localhost:3000/.

---
