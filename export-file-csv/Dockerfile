FROM python:3.8-alpine

# Copy the worker
COPY src /opt/opencti-connector-export-file-csv

# Install Python modules
# hadolint ignore=DL3003
RUN apk --no-cache add git build-base libmagic libffi-dev && \
    cd /opt/opencti-connector-export-file-csv && \
    pip3 install --no-cache-dir git+https://github.com/OpenCTI-Platform/client-python@4.1.2 && \
    pip3 install --no-cache-dir -r requirements.txt && \
    apk del git build-base

# Expose and entrypoint
COPY entrypoint.sh /
RUN chmod +x /entrypoint.sh 
ENTRYPOINT ["/entrypoint.sh"]
