

# 1. Create Custom Dockerfile and Push to Docker Hub

I’ll guide you step-by-step inside **VS Code**.

---

## ✅ STEP 1: Create Project Folder

Create a folder anywhere on your PC:

```bash id="sd2r19"
docker-project
```

Open this folder in **Visual Studio Code**

---

## ✅ STEP 2: Create 3 Files Inside Folder

Inside VS Code Explorer:

Create these files:

```bash id="u6a0fj"
app.py
requirements.txt
Dockerfile
```

---

## ✅ STEP 3: Paste Code in Each File

---

## 📌 app.py

```python id="kfpj5l"
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Docker"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

---

## 📌 requirements.txt

```txt id="5hhx6c"
flask
```

---

## 📌 Dockerfile

```dockerfile id="lq2qz8"
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

CMD ["python", "app.py"]
```

---

## ✅ STEP 4: Save All Files

Press:

```bash id="wyfd0h"
Ctrl + S
```

---

## ✅ STEP 5: Open Terminal in VS Code

Click:

```bash id="x82f1m"
Terminal > New Terminal
```

---

## ✅ STEP 6: Build Docker Image

Run:

```bash id="2u3w8l"
docker build -t yourusername/myapp:latest .
```

⚠ Replace `yourusername` with your Docker Hub username.

Example:

```bash id="83ot5u"
docker build -t rahul123/myapp:latest .
```

---

## ✅ STEP 7: Run Container (Test)

```bash id="x5ov56"
docker run -p 5000:5000 yourusername/myapp:latest
```

Now open browser:

```bash id="q0ec4g"
http://localhost:5000
```

You’ll see:

```bash id="hh80o4"
Hello from Docker
```

---

## ✅ STEP 8: Login Docker Hub

Run:

```bash id="08w4ln"
docker login
```

Enter username + password.

---

## ✅ STEP 9: Push Image to Docker Hub

Run:

```bash id="zj74lm"
docker push yourusername/myapp:latest
```

---

## ✅ STEP 10: Submit Link

Your Docker Hub image link:

```bash id="4qn0pj"
https://hub.docker.com/r/yourusername/myapp
```

---

