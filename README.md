# Ads Application (Diploma Project)

## Описание

Это серверная часть веб-приложения для размещения объявлений.  
Проект реализован в рамках финального дипломного задания на курсе Java-разработки от Skypro.

Сервис поддерживает регистрацию, авторизацию, работу с объявлениями и комментариями, хранение изображений, а также разграничение прав доступа по ролям пользователей (`USER`, `ADMIN`).

## Используемые технологии

- Java 17
- Spring Boot 3.3.3
- Spring Security
- Spring Data JPA
- MapStruct
- Liquibase
- PostgreSQL
- Docker
- Swagger / OpenAPI
- Lombok

## Архитектура

Приложение реализовано по принципам MVC.

- `controller` — REST-контроллеры, принимающие и возвращающие DTO.
- `dto` — классы передачи данных между клиентом и сервером.
- `entity` / `model` — JPA-сущности, соответствующие таблицам БД.
- `repository` — интерфейсы Spring Data JPA для работы с БД.
- `service` — бизнес-логика.
- `mapper` — MapStruct-классы, преобразующие между DTO и Entity.
- `config` — конфигурация Spring Security, Swagger, Liquibase.

## Аутентификация и авторизация

- Используется Basic-аутентификация.
- Пользователи хранятся в PostgreSQL.
- Поддерживаются две роли:
  - `USER`: может управлять своими объявлениями и комментариями.
  - `ADMIN`: имеет расширенные права (в том числе редактирование и удаление чужих данных).

## Работа с базой данных

- СУБД: PostgreSQL
- Миграции: Liquibase
- Схема создается автоматически на старте приложения
- `spring.jpa.hibernate.ddl-auto=validate`

## 💬 API документация

Swagger UI доступен по адресу:  
[http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)

## Участник проекта

- Долинская Алина 
  - Роль: разработка, настройка БД, безопасность, интеграция с фронтом, деплой

## Запуск проекта

```bash
# Запуск БД (Docker)
docker run --name ads-pg \
  -e POSTGRES_USER=postgres \
  -e POSTGRES_PASSWORD=postgres \
  -e POSTGRES_DB=ads \
  -p 5432:5432 -d postgres:16

# Сборка проекта
./mvnw clean install

# Запуск приложения
./mvnw spring-boot:run

```

