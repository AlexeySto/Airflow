# Airflow

Airflow — это инструмент для создания, управления и мониторинга рабочих процессов (pipeline). Он идеально подходит для ETL-задач и MLOps. Например, для извлечения данных из различных источников, их агрегации, преобразования и хранения в хранилище данных.

## О проекте

Целью проекта было создание надежной и масштабируемой системы управления рабочими процессами. Airflow позволяет определять рабочие процессы с использованием Directed Acyclic Graphs (DAGs), запускать их в соответствии с расписанием и мониторить их выполнение. Проект предоставляет веб-интерфейс для управления рабочими процессами, а также поддерживает различные типы исполнителей (executors) для локального и распределенного выполнения задач.

## Инструкция по развертыванию

1. **Установка Airflow**
   - Используйте следующие команды для установки Airflow с использованием Docker Compose:
     ```bash
     curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.5.1/docker-compose.yaml'
     docker-compose up -d
     ```
   - Если вы хотите установить Airflow без использования Docker, вы можете использовать pip:
     ```bash
     AIRFLOW_VERSION=2.7.2
     PYTHON_VERSION="$(python --version | cut -d " " -f 2 | cut -d "." -f 1-2)"
     CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"
     pip install "apache-airflow==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"
     ```

2. **Инициализация базы данных**
   - После установки Airflow выполните следующую команду для инициализации базы данных:
     ```bash
     airflow db migrate
     ```

3. **Запуск веб-сервера**
   - Запустите веб-сервер Airflow:
     ```bash
     airflow webserver
     ```

4. **Запуск планировщика**
   - Запустите планировщик Airflow:
     ```bash
     airflow scheduler
     ```

5. **Доступ к веб-интерфейсу**
   - Откройте веб-интерфейс Airflow в браузере по адресу `http://localhost:8080/`.

## Используемые технологии

- **Apache Airflow**: платформа для создания и управления рабочими процессами.
- **Docker**: контейнерная технология для деплоя и запуска Airflow.
- **Python**: основной язык программирования для написания DAGs.

## Автор

- **Alexey Sto**: [GitHub](https://github.com/AlexeySto)
