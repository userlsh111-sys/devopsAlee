FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . . 

ENV APP_TITLE="InhaTC DevOps 방명록" \
    THEME_COLOR="#0054A6"

EXPOSE 5000

CMD ["python", "app.py"]
