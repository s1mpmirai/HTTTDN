FROM python:3.11-slim

WORKDIR /app

# Cài dependencies trước để tận dụng Docker cache
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy toàn bộ source code
COPY . .

EXPOSE 8000

# Chạy với reload để hot-reload khi dev
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
