FROM alpine

RUN apk add --no-cache python3 && \
    python3 -m ensurepip && \
    rm -r /usr/lib/python*/ensurepip && \
    pip3 install --upgrade pip setuptools && \
    if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi && \
    rm -r /root/.cache && \
    rm -rf /var/cache/apk/*

WORKDIR /app
COPY ./app /app
RUN pip3 --no-cache-dir install flask boto3

EXPOSE 80
CMD python3 app.py
