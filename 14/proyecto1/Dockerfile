FROM ubuntu:20.04
LABEL Creator: "juanpgarza"

RUN apt-get update \
    && apt-get upgrade -y

RUN apt-get install -y \
    openssh-server fail2ban

RUN adduser --disabled-password --gecos "Odoo" odoo

RUN apt-get install -y \
    python3-pip

RUN apt-get install -y python-dev python3-dev libxml2-dev libxslt1-dev zlib1g-dev libsasl2-dev libldap2-dev build-essential libssl-dev libffi-dev libmysqlclient-dev libjpeg-dev libpq-dev libjpeg8-dev liblcms2-dev libblas-dev libatlas-base-dev

WORKDIR /opt/odoo

COPY src/requirements.txt .

RUN pip3 install -r requirements.txt

RUN apt-get update \
    && \
    apt-get install -y \
    nano

RUN pip3 install pyopenssl
