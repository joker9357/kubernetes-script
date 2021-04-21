FROM alpine:3.9 

# Technical account
ARG UID=12345
ARG GID=54321

COPY go-test /app/go-test-app

USER root
# Create new user and group
RUN mkdir /lib64 && \
    ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2 && \
    addgroup -g $GID rungroup && \
    adduser runuser -u $UID -G rungroup -D -H && \
    chmod 755 /app/go-test-app && \
    chown -R runuser:rungroup /app
	
USER runuser

# Exposes port 3000
EXPOSE 3000

ENTRYPOINT ["/app/go-test-app"]