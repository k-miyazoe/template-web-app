FROM python:3.9-slim

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# 必要なシステムライブラリをインストール
RUN apt-get update && apt-get install -y \
    build-essential \
    default-libmysqlclient-dev \
    libssl-dev \
    libffi-dev \
    && apt-get clean

WORKDIR /app

COPY requirements.txt .

RUN apt-get update && apt-get install -y gcc
RUN pip install --upgrade pip 
RUN pip install --no-cache-dir -r requirements.txt

CMD ["uvicorn", "main:app", "--reload", "--host", "0.0.0.0", "--port", "8005"]