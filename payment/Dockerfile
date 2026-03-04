FROM python:3.9
EXPOSE 8080
WORKDIR /opt/server
# Build deps for uwsgi & friends
COPY payment.ini .
COPY *.py .
# Only requirements first for caching
COPY requirements.txt .
# Install into /install (just like you did)
RUN pip3 install --prefix=/install -r requirements.txt
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
CMD ["uwsgi", "--ini", "payment.ini"]    