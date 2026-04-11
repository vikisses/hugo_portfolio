---
title: "HTTP. Клиент-серверное взаимодействие"
date: 2026-04-11
draft: false
---

# Лабораторная работа: Протокол HTTP

---

Я выбирала сайт с ресурса - https://free-apis.github.io/#/browse  
Мой выбор упал на - https://httpbin.org/  
Выбрала его, т к он не требует API key   

## 1. GET-запрос через Telnet

```bash
telnet httpbin.org 80
```

```http
GET /get HTTP/1.1
Host: httpbin.org
```
Ответ: сервер вернул статус 200 OK и JSON-данные с информацией о запросе.
![Telnet GET](images/telnet_get.png)

---

## 2. POST-запрос через Telnet

```http
POST /post HTTP/1.1
Host: httpbin.org
Content-Type: application/json
Content-Length: 31

{"name":"vika","job":"student"}
```
Ответ: сервер вернул статус 200 OK и отправленные данные.
![Telnet POST](/images/telnet_post.png)

---

## 3. GET-запрос через cURL

```bash
curl https://httpbin.org/get
```
Ответ: получен JSON с параметрами запроса.
![curl GET](/images/curl_get.png)

---

## 4. POST-запрос через curl

```bash
curl -X POST https://httpbin.org/post \
-H "Content-Type: application/json" \
-d '{"name":"vika","job":"student"}'
```

---

Ответ:
```xml
<?xml version="1.0" encoding="windows-1251"?>
<ValCurs ID="R01235" DateRange1="01.03.2025" DateRange2="10.03.2025" name="Foreign Currency Market Dynamic">
    <Record Date="01.03.2025" Id="R01235">
        <Nominal>1</Nominal>
        <Value>88,2568</Value>
        <VunitRate>88,2568</VunitRate>
    </Record>
    <Record Date="04.03.2025" Id="R01235">
        <Nominal>1</Nominal>
        <Value>89,2497</Value>
        <VunitRate>89,2497</VunitRate>
    </Record>
    <Record Date="05.03.2025" Id="R01235">
        <Nominal>1</Nominal>
        <Value>89,2448</Value>
        <VunitRate>89,2448</VunitRate>
    </Record>
    <Record Date="06.03.2025" Id="R01235">
        <Nominal>1</Nominal>
        <Value>89,7878</Value>
        <VunitRate>89,7878</VunitRate>
    </Record>
    <Record Date="07.03.2025" Id="R01235">
        <Nominal>1</Nominal>
        <Value>89,5724</Value>
        <VunitRate>89,5724</VunitRate>
    </Record>
    <Record Date="08.03.2025" Id="R01235">
        <Nominal>1</Nominal>
        <Value>89,1362</Value>
        <VunitRate>89,1362</VunitRate>
    </Record>
</ValCurs>
```
![curl POST](/images/curl_post.png)

## 5. GET-запрос к API Банка России (Postman)  
Офицальная документация API ЦБ: https://www.cbr.ru/development/sxml/  
API Центрального Банка: https://www.cbr.ru/scripts/XML_dynamic.asp  
Дата начала: date_req1=01/03/2025  
Дата конца: date_req2=10/03/2025  
Код валюты (доллар США): VAL_NM_RQ=R01235  
Запрос такой будет: курс доллара с 1 по 10 марта 2025  


```text
[https://www.cbr.ru/scripts/XML_dynamic.asp?date_req1=01/03/2025&date_req2=10/03/2025&VAL_NM_RQ=R01235](https://www.cbr.ru/scripts/XML_dynamic.asp?date_req1=01/03/2025&date_req2=10/03/2025&VAL_NM_RQ=R01235)
```
![Postman](/images/load_postman.png)
![Postman](/images/postman_menu.png)
![Postman](/images/get_postman.png)


---
