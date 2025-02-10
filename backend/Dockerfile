FROM python:3.9

# Создание рабочей директории внутри контейнера
WORKDIR /app

RUN pip install gunicorn==20.1.0

# Копирование файла зависимостей в контейнер
COPY requirements.txt /app

# Установка зависимостей
RUN pip install -r requirements.txt --no-cache-dir

# Копирование всех файлов проекта в контейнер
COPY . /app

# Указание команды для запуска приложения при старте контейнера
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"] 
