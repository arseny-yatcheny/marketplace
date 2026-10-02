FROM python:3.12-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

WORKDIR /app
COPY main.py ./main.py

USER 10001:10001
EXPOSE 8080

HEALTHCHECK --interval=15s --timeout=3s --start-period=5s --retries=3 \
    CMD ["python", "-c", "import json, urllib.request; r = urllib.request.urlopen('http://127.0.0.1:8080/health', timeout=2); assert r.status == 200; assert r.headers.get_content_type() == 'application/json'; assert json.load(r) == {'status': 'ok'}"]

CMD ["python", "main.py"]
