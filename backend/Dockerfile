FROM python:3.12-slim-bullseye

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . .

# Install Poetry
RUN pip install poetry

# Disable creation of virtual environments by poetry as Docker is already isolated
RUN poetry config virtualenvs.create false

# Install project dependencies
RUN poetry install --no-dev

# Expose the port Uvicorn will listen on
EXPOSE 7001

# Command to run the Uvicorn server
CMD ["poetry", "run", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "7001"]
