FROM python:3.9

ENV PYTHONUNBUFFERED=TRUE

RUN pip --no-cache-dir install pipenv

WORKDIR /prediction

COPY ["Pipfile", "Pipfile.lock", "./"]
RUN pipenv install --deploy --system && \
    rm -rf /root/.cache

COPY ["*.py", "churn-model.bin", "./"]

EXPOSE 2525

ENTRYPOINT ["gunicorn", "--bind", "0.0.0.0:2525", "churn_serving:app"] 
