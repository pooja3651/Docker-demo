# Use Amazon Linux as the base image
FROM amazonlinux:latest

# Set the working directory in the image
WORKDIR /app

# Copy the files from the host to the image
COPY . /app

# Install necessary packages using yum
RUN yum update -y && yum install -y python3 python3-pip

# Set environment variables
ENV NAME World

# Run a command to start the application
CMD ["python3", "app.py"]

