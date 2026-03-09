# 🚀 Training Ecosystem — Microservices Platform

Высоконагруженная микросервисная система для управления тренировками, упражнениями и питанием.

Проект реализован на **Java + Spring Boot** и демонстрирует современную backend-архитектуру:

- Microservices Architecture
- Event Driven Architecture
- Distributed Systems
- High Scalability
- High Availability

Система состоит из **7 независимых сервисов**, взаимодействующих через **API Gateway**, **Service Discovery** и **Kafka events**.

---

# 🏗 Архитектура системы

Архитектура построена на принципах **микросервисного подхода**, где каждый сервис отвечает за свою область бизнес-логики.

Основные принципы:

- независимое масштабирование сервисов  
- слабая связность (loose coupling)  
- асинхронное взаимодействие через события  
- отказоустойчивость системы  

## Общая схема

```
Client
   │
   ▼
API Gateway
   │
   ▼
Service Discovery (Eureka)
   │
   ├── Training Service
   ├── Trains Service
   ├── Nutrition Service
   ├── Recommendation Service
   └── Notification Service
```

Инфраструктурные компоненты:

- PostgreSQL
- Redis
- Elasticsearch
- Apache Kafka
- Docker

---

# 🧠 Основные технологические решения

## 🔍 Elasticsearch — Full Text Search

Используется для **быстрого поиска тренировок и упражнений**.

Позволяет:

- выполнять поиск по неполному совпадению
- фильтровать данные по различным параметрам
- выполнять сложные поисковые запросы

Это значительно быстрее обычных SQL запросов при работе с большим количеством данных.

---

## ⚡ Redis — Distributed Cache

Redis используется как **in-memory кэш**.

Позволяет:

- ускорить получение данных
- снизить нагрузку на PostgreSQL
- хранить часто используемые данные

Примеры использования:

- кэширование данных о питании
- ускорение вычислений КБЖУ

---

## 📡 Apache Kafka — Event Driven Communication

Сервисы взаимодействуют **асинхронно через события**.

Преимущества:

- слабая связность сервисов
- высокая устойчивость системы
- возможность обработки событий в реальном времени

Пример взаимодействия:

```
Training Service → Kafka → Notification Service
```

Когда создается новая тренировка, отправляется событие, и Notification Service отправляет уведомление пользователю.

---

## 🌐 API Gateway

API Gateway является **единой точкой входа в систему**.

Функции:

- маршрутизация запросов
- балансировка нагрузки
- CORS конфигурация
- централизованный доступ к сервисам

Все клиентские запросы проходят через Gateway.

---

## 🔎 Service Discovery (Eureka)

Используется для **динамического обнаружения сервисов**.

Каждый сервис:

- регистрируется в Eureka
- получает список других сервисов

Это позволяет системе автоматически масштабироваться.

---

# 🔍 Микросервисы проекта

## 🌐 API Gateway

Repository  
https://github.com/Maru3022/API_Gateway

Технологии:

- Spring Cloud Gateway
- Spring Boot

Функции:

- единая точка входа
- маршрутизация запросов
- проксирование запросов к сервисам

---

## 🔎 Eureka Server

Repository  
https://github.com/Maru3022/Eureka-server

Технологии:

- Spring Cloud Netflix Eureka

Функции:

- регистрация сервисов
- обнаружение сервисов
- балансировка нагрузки

Каждый сервис автоматически регистрируется в системе.

---

## 🏋 Training Service

Repository  
https://github.com/Maru3022/Training-Servive

Технологии:

- Java
- Spring Boot
- Spring Data JPA
- PostgreSQL

Функции:

- хранение базы упражнений
- управление тренировками
- CRUD операции

Основной сервис для управления тренировочными программами.

---

## 🔍 Trains Service

Repository  
https://github.com/Maru3022/Trains-Service

Технологии:

- Java
- Spring Boot
- Elasticsearch

Функции:

- быстрый поиск тренировок
- фильтрация программ
- full text search

Сервис оптимизирован для быстрого поиска данных.

---

## 🥗 Nutrition Service

Repository  
https://github.com/Maru3022/Training-Nutrition

Технологии:

- Java
- Spring Boot
- PostgreSQL
- Redis

Функции:

- управление питанием
- расчет КБЖУ
- кэширование данных

Redis используется для ускорения обработки данных.

---

## 🤖 Recommendation Service

Repository  
https://github.com/Maru3022/Recommendation-Service

Технологии:

- Java
- Spring Boot
- Spring Data JPA
- PostgreSQL

Функции:

- рекомендации тренировок
- анализ активности пользователя
- генерация персональных программ

Сервис реализует алгоритмический подбор тренировок.

---

## 🔔 Notification Service

Repository  
https://github.com/Maru3022/Training_Notification

Технологии:

- Java
- Spring Boot
- Apache Kafka

Функции:

- обработка событий из Kafka
- отправка уведомлений
- асинхронная обработка данных

---

# 🧰 Полный стек технологий

### Backend

- Java 17 / 21
- Spring Boot 3
- Spring Data JPA
- Spring Cloud

### Infrastructure

- Spring Cloud Gateway
- Netflix Eureka

### Databases

- PostgreSQL
- Redis
- Elasticsearch

### Messaging

- Apache Kafka

### DevOps

- Docker
- Docker Compose

---

# 🐳 Запуск проекта

### 1. Клонировать репозитории

```
git clone https://github.com/Maru3022/API_Gateway
git clone https://github.com/Maru3022/Eureka-server
git clone https://github.com/Maru3022/Training-Servive
git clone https://github.com/Maru3022/Trains-Service
git clone https://github.com/Maru3022/Training-Nutrition
git clone https://github.com/Maru3022/Recommendation-Service
git clone https://github.com/Maru3022/Training_Notification
```

---

### 2. Запустить инфраструктуру

```
docker-compose up -d
```

Это автоматически поднимет:

- PostgreSQL
- Redis
- Kafka
- Elasticsearch
- все микросервисы

---

# 📈 Цель проекта

Основная цель проекта — продемонстрировать навыки разработки:

- микросервисной архитектуры
- распределенных систем
- высоконагруженных backend сервисов
- работы с современным Java стеком

Проект является примером **production-like backend системы**, включающей caching, messaging, search engine и service discovery.
