# Use an official Python runtime as a parent image
FROM python:3.12

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set the working directory in the container
WORKDIR /code

# Copy the requirements file into the container
COPY requirements.txt /code/

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy the current directory contents into the container at /code/
COPY . /code/

# Make port 8000 available to the world outside this container
EXPOSE 8000

# Define environment variable
# ENV DJANGO_SETTINGS_MODULE=todoproject.settings

# Run database migrations and start the Django server
CMD ["sh", "-c", "python manage.py makemigrations && python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]