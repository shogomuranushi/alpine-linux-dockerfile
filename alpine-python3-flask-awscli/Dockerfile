FROM alpine

RUN apk add --no-cache python3 && \
    python3 -m ensurepip && \
    rm -r /usr/lib/python*/ensurepip && \
    pip3 install --upgrade pip setuptools && \
    if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi && \
    rm -r /root/.cache

WORKDIR /app
COPY ./app /app
RUN pip3 install flask

RUN apk --no-cache update && \
    apk --no-cache add ca-certificates curl groff less && \
    pip3 --no-cache-dir install awscli && \
    rm -rf /var/cache/apk/*

EXPOSE 80
CMD python3 app.py
