FROM python:3.11-slim-buster

COPY ./container/python/requirements.txt /tmp
RUN pip install -r /tmp/requirements.txt
WORKDIR /app
CMD ["uvicorn", "api_pearson.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
