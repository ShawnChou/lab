FROM python:alpine3.7
# 修改alpine系统源及pip安装源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
RUN mkdir -p /root/.pip
RUN echo -e "[global]\nindex-url = https://mirrors.aliyun.com/pypi/simple/" > /root/.pip/pip.conf
# 安装gcc编译环境
RUN apk add --no-cache build-base
# 安装支持http/https协议客户端请求库
RUN pip install requests &&\
    pip install aiohttp &&\
    pip install tornado &&\
    pip install selenium &&\
    pip install appium-python-client
# 下列模块的安装需要gcc编译环境
RUN pip install twisted &&\
    pip install gevent==1.4.0
# 安装scrapy
RUN apk add --no-cache libxml2-dev libxslt-dev zlib-dev libffi-dev openssl-dev &&\
    pip install scrapy
# 安装pyspider
RUN apk add --no-cache curl-dev openssl-dev libxml2-dev libxslt-dev zlib-dev &&\
    pip install pyspider &&\
    apk del build-base
