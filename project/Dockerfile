#拉取python官方瘦身镜像
FROM python:3.10.1-slim-buster

#设定工作目录
WORKDIR /usr/src/app

#设置环境变量
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

#安装系统依赖
RUN apt-get update \
  && apt-get -y install netcat gcc \
  && apt-get clean \

#安装python项目依赖
RUN pip install --upgrade pip
COPY ./requirements.txt .
RUN pip install -r requirements.txt

# 添加应用（把所有的的文件复制入工作目录）
COPY . .

# add entrypoint.sh
COPY ./entrypoint.sh .
RUN chmod +x /usr/src/app/entrypoint.sh

# run entrypoint.sh
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]