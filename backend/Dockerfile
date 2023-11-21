FROM python:3.12-slim-bullseye

ENV POETRY_VERSION 1.4.1

# Install system dependencies
RUN pip install "poetry==$POETRY_VERSION"

# Set work directory
WORKDIR /app

# Copy only requirements to cache them in docker layer
RUN pip install poetry

# Disable creation of virtual environments by poetry as Docker is already isolated
RUN poetry config virtualenvs.create false

# Install project dependencies
RUN poetry install --no-dev

# Copy the current directory contents into the container at /app
COPY ./ /app/

EXPOSE 7001

CMD ["poetry", "run", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "7001"]
