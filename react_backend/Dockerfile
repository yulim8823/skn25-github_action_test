FROM python:3.12-slim

WORKDIR /app

ENV DJANGO_SETTINGS_MODULE=react_backend.settings.development
ENV PYTHONUNBUFFERED=1
ENV PYTHONDONTWRITEBYTECODE=1
RUN apt-get update && apt-get install -y \
    gcc \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["gunicorn", "react_backend.wsgi:application", "--bind", "0.0.0.0:8001", "--workers", "2"]
