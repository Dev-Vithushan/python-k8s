FROM ubuntu:latest

WORKDIR /app

# Copy the requirements file and application code
COPY requirements.txt /app
COPY devops /app

# Update apt sources and install required packages
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv && \
    python3 -m venv /app/venv

# Activate the virtual environment and install Python packages
RUN /app/venv/bin/pip install --upgrade pip && \
    /app/venv/bin/pip install -r requirements.txt

# Set the default Python path to use the virtual environment
ENV PATH="/app/venv/bin:$PATH"

# Define the entry point for the Django application
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
