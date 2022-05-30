FROM python:3

ENV PYTHONUNBUFFERED 1
RUN mkdir /code
WORKDIR /code
COPY . /code/
COPY Pipfile Pipfile.lock ./

RUN python -m pip install --upgrade pip
RUN pip install psycopg2-binary
RUN pip install gunicorn
RUN pip install pipenv && pipenv install --dev --system --deploy

EXPOSE 8000
CMD ["gunicorn", "--chdir", "swe573_2022_repo", "--bind", ":8000", "colearning.wsgi:application", "--reload"] 	

