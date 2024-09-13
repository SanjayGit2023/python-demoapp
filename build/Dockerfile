# Use an official Python runtime as a parent image
FROM python:3.9-slim-buster

# Define metadata using LABEL (correct key=value format)
LABEL Name="Python Flask Demo App" \
      Version="1.4.2" \
      org.opencontainers.image.source="https://github.com/SanjayGit2023/python-demoapp.git"

# Set argument for source directory to copy files from
ARG srcDir=src

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file and install dependencies
COPY $srcDir/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application
COPY $srcDir/run.py .
COPY $srcDir/app ./app

# Make port 5000 available to the world outside this container
EXPOSE 5000

# Define the command to run the app using Gunicorn
CMD ["gunicorn", "-b", "0.0.0.0:5000", "run:app"]

