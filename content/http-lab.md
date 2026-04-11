---
title: "HTTP. Клиент-серверное взаимодействие"
date: 2026-04-11
---

# Лабораторная работа: Протокол HTTP

---

## 1. GET-запрос через netcat

```bash
ncat --ssl reqres.in 443
```

```http
GET /api/users/2 HTTP/1.1
Host: reqres.in
```

---

## 2. POST-запрос через netcat

```http
POST /api/users HTTP/1.1
Host: reqres.in
Content-Type: application/json
Content-Length: 31

{"name":"vika","job":"student"}
```

---

## 3. GET-запрос через curl

```bash
curl https://reqres.in/api/users/2
```

---

## 4. POST-запрос через curl

```bash
curl -X POST https://reqres.in/api/users \
-H "Content-Type: application/json" \
-d '{"name":"vika","job":"student"}'
```

---

## 5. GET-запрос к API Банка России (Postman)

```text
https://www.cbr.ru/scripts/XML_dynamic.asp?date_req1=01/03/2025&date_req2=10/03/2025&VAL_NM_RQ=R01235
```

---
