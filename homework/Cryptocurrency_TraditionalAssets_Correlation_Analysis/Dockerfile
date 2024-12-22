FROM python:3.10-slim

WORKDIR /app
RUN mkdir -p /app/results

COPY requirements.txt .

RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

COPY src/data /app/src/data
# 复制模型脚本
COPY src/models /app/src/models
COPY src/visualization /app/src/visualization
# 安装 Jupyter
RUN pip install jupyter nbconvert

# 设置默认命令运行 Jupyter
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
CMD ["python", "src/main.py"]

docker build -t crypto-correlation .
docker run -p 8888:8888 crypto-correlation
