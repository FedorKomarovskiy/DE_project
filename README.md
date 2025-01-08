# DE_project

## Описание

Проект **DE_project** представляет собой систему для управления данными в базе данных PostgreSQL с использованием Docker-контейнера. В рамках проекта реализованы модули для генерации данных, их инициализации и работы с различными сущностями, такими как пользователи, товары, заказы, отзывы и бонусные баллы.

## Структура проекта

Проект состоит из нескольких ключевых компонентов:

- **data_generation**: Модуль для генерации данных.
- **db_schems**: Схемы для таблиц в базе данных.
- **docker**: Конфигурация Docker для запуска базы данных.
- **postgresdb**: Модуль для работы с PostgreSQL.
- **requirements.txt**: Список зависимостей для проекта.
- **main.py**: Основной файл для запуска приложения.

### Структура базы данных

В проекте используется база данных **PostgreSQL** с следующими таблицами:

- **Users**: Информация о пользователях.
  - `user_id` (PK), `first_name`, `last_name`, `email`, `phone`, `registration_date`, `loyalty_status`
  
- **ProductCategories**: Иерархия категорий товаров.
  - `category_id` (PK), `name`, `parent_category_id` (FK)

- **Products**: Информация о товарах.
  - `product_id` (PK), `name`, `description`, `category_id` (FK), `price`, `stock_quantity`, `creation_date`

- **Orders**: Информация о заказах.
  - `order_id` (PK), `user_id` (FK), `order_date`, `total_amount`, `status`, `delivery_date`

- **OrderDetails**: Детали заказов.
  - `order_detail_id` (PK), `order_id` (FK), `product_id` (FK), `quantity`, `price_per_unit`, `total_price`

- **Reviews**: Отзывы о товарах.
  - `review_id` (PK), `user_id` (FK), `product_id` (FK), `rating`, `review_text`, `created_at`

- **LoyaltyPoints**: Система лояльности.
  - `loyalty_id` (PK), `user_id` (FK), `points`, `reason`, `created_at`

## Установка и настройка

Для начала работы с проектом выполните следующие шаги:

1. **Клонируйте репозиторий**:
    ```bash
    git clone https://github.com/FedorKomarovskiy/DE_project.git
    cd DE_project
    ```

2. **Запустите Docker-контейнер с PostgreSQL**:
    Для автоматического запуска базы данных PostgreSQL используйте команду:
    ```bash
    docker-compose up -d
    ```

3. **Проверьте состояние контейнера**:
    Убедитесь, что контейнер работает:
    ```bash
    docker ps
    ```
    База данных должна быть доступна по следующим параметрам:
    - Хост: `localhost`
    - Порт: `5432`
    - Имя базы данных: `postgresdb`
    - Имя пользователя: `postgres`
    - Пароль: `qwerty`

4. **Запустите модуль генерации данных**:
    Для наполнения базы данных данными выполните скрипт:
    ```bash
    python data_generation/generator.py
    ```

    Это создаст пользователей, товары, категории, заказы, отзывы и бонусные баллы в базе данных.

## Запуск проекта

Для работы с проектом используйте основной файл **main.py**.

1. Убедитесь, что все зависимости установлены:
    ```bash
    pip install -r requirements.txt
    ```

2. Запустите проект:
    ```bash
    python main.py
    ```

## Управление версией

Проект использует **Git** для контроля версий. Вот основные команды:

- **Получить последние изменения**:
    ```bash
    git pull https://github.com/FedorKomarovskiy/DE_project
    ```

- **Коммит изменений**:
    ```bash
    git commit -m "Project finished"
    ```

- **Отправить изменения на GitHub**:
    ```bash
    git push
    ```

