# Use Amazon Linux 2 as the base image
FROM amazonlinux:2

# Set environment variables to avoid interactive prompts
ENV TERM=xterm

# Install Apache HTTP Server using yum
RUN yum -y update && \
    yum -y install httpd && \
    yum clean all

# Set /var/www/html as the working directory
WORKDIR /var/www/html/

# Copy the website files into the Apache root directory (renamed to coffee)
COPY tea/ /var/www/html/

# Adjust permissions
RUN chmod -R 755 /var/www/html

# Configure Apache (optional)
RUN echo "ServerName localhost" >> /etc/httpd/conf/httpd.conf

# Expose port 81
EXPOSE 81

# Start Apache in the foreground
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
