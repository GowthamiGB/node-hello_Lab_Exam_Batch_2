# Use an official Ubuntu 18.04 image as base
FROM ubuntu:18.04

# Set environment variable to avoid interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Update package lists and install necessary packages
RUN apt-get update && \
    apt-get install -y \
        apache2 \
        php \
        libapache2-mod-php \
        nodejs \
        npm && \
    apt-get clean

# Change Apache configuration if needed
# COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

# Install Node.js packages if required
# RUN npm install -g pm2

# Expose port 80 (default HTTP port)
EXPOSE 80

# Start Apache server
CMD ["apachectl", "-D", "FOREGROUND"]

