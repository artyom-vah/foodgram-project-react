FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .

RUN apt-get update

RUN apt-get upgrade -y

RUN pip install --upgrade pip

RUN pip install -r requirements.txt

COPY . .

# RUN apt-get update && apt-get upgrade -y && \
#     pip install --upgrade pip && pip install -r requirements.txt

CMD ["gunicorn", "foodgram.wsgi:application", "--bind", "0:8000" ]