# Goal: Build a Docker image and push it to Docker Hub. 

**Step 1: Create Project Files**
Create a folder with the following two files: app.py 

Python 
```
from flask import Flask 
app = Flask(__name__)
 
@app.route('/') 
def home(): 
 return "Hello from Docker"

if __name__ == '__main__':
 app.run(host='0.0.0.0', port=5000)
```

requirements.txt 
Plaintext 
flask

**Step 2: Create Dockerfile**

Dockerfile 
```
FROM python:3.9-slim 
WORKDIR /app 
COPY requirements.txt . 
RUN pip install -r requirements.txt 
COPY . . 
CMD ["python", "app.py"]

Step 3: Build and Push 
1. Build: docker build -t yourusername/myapp:latest . 
2. Login: docker login 
3. Push: docker push yourusername/myapp:latest
