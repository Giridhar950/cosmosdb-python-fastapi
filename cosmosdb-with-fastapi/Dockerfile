FROM python:3.9
WORKDIR /code
COPY ./requirements.txt /code/requirements.txt

RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt

COPY . /code

ARG DB_URI='testuri'
ARG DB_KEY='secret'
ARG DB_CONN_STR='teststr'
ARG INSIGHTS_KEY='testkey'
ENV URI=$DB_URI \
    KEY=$DB_KEY \
    AZURE_COSMOS_CONNECTION_STRING=$DB_CONN_STR \
    APPINSIGHTS_INSTRUMENTATIONKEY=$INSIGHTS_KEY

EXPOSE 3100

HEALTHCHECK --interval=12s --timeout=12s --start-period=30s \
            CMD curl http://127.0.0.1:3100

CMD ["uvicorn", "main:app", "--reload", "--host", "0.0.0.0", "--port", "3100"]