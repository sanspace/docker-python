#### 🐳 Dockerize a Python App 🐍

🎬 [**San**](https://sanspace.in)thosh Srinivasan

---

#### What? 🚢

  - Dockerize a Python App
  - How to create a Dockerfile?
  - How to create a Docker Image?
  - How to create/run a Docker Container?



#### Why?

  - No more "it works on my machine"
  - consistent, reproducible images everytime
  - Your code, dependencies and runtime all bundled together
  - It's as easy as it should be!
  - great for microservices



  - efficient use of system resources
  - run apps as if they run on diff servers
  - faster software delivery life cycle
  - excellent portability



#### How?

  Let's have a demo!

---

#### Before Docker

Sharing Python App without Docker



#### Code

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0')
```



#### Dependencies

  - Use venv to create virtual env
    
    `python -m venv venv`
  - Use pip to install requirements
    
    `pip install Flask`
  - Freeze your requirements
    
    `pip freeze > requirements.txt`



#### Prep the repo

  - `.gitignore` venv
  - check in `requirements.txt` along with your code
  - write an awesome `README`



#### Runtime

  A VM / Virtualbox perhaps?

  - Too heavy and resource hogging
  - Very slow boottimes and even run times
  - Includes a full Operating System

---

#### After Docker

  - write code
  - install and use dependencies
  - __write a Dockerfile__
  - __build a Docker Image__
  - Publish/Share the Image



#### Let's dock

```dockerfile
# comment
INSTRUCTION arguments
```



#### Our Dockerfile

```dockerfile
FROM python:3.9.2-alpine3.13

LABEL maintainer="san@sanspace.in"

# We copy just the requirements.txt first to leverage Docker cache
COPY ./requirements.txt /app/requirements.txt

WORKDIR /app

RUN pip install -r requirements.txt

COPY . /app

ENTRYPOINT [ "python" ]

CMD [ "app.py" ]
```



#### Build and Run

Build and Tag:

`docker build -t demo:latest .`

Run Docker Container from Image:

`docker run -d -p 5000:5000 demo`

---

#### Resources 🔖

  - [Docker 101](https://www.docker.com/101-tutorial)
  - Dockerfile [reference](https://docs.docker.com/engine/reference/builder/)

---

#### Feedback 🗣️

  - This deck is on [Github](https://github.com/sanspace/docker-python). Issues/PRs are appreciated!
  - Reach out to [me](https://sanspace.in).
