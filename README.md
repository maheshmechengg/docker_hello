# docker_hello


```bash
cd /path/to/python-docker
pip3 install Flask
pip3 freeze > requirements.txt
touch app.py
```

Create app.py
```bash
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, Docker!'
```

Create Dockerfile
```bash
# syntax=docker/dockerfile:1

FROM python:3.8-slim-buster

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]
```

Build docker
```bash
docker build -t(tag) my_hello .
```

run docker

```bash
docker run -p 8000:8000 my_hello
```

Open another terminal & get running dockers
```bash
docker ps
```

Get ip address of runninh docker
```bash
docker inspect <docker_id>
```




