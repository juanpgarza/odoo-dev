FROM ubuntu:16.04
LABEL Creator: "juanpgarza"

RUN apt-get update \
    && \
    apt-get install -y npm \
    && \
    ln -s /usr/bin/nodejs /usr/bin/node \
    && \
    npm install -g less less-plugin-clean-css

RUN adduser --disabled-password --gecos "Odoo" odoo

RUN apt-get update \
    && \
    apt-get install -y \
    nano \
    git \
    python3-dev \
    python3-pip \
    libxml2-dev \
    libxslt1-dev \
    libevent-dev \
    libsasl2-dev \
    libldap2-dev \
    libpq-dev \
    libpng12-dev \
    libjpeg-dev \
    poppler-utils \
    node-less \
    node-clean-css

RUN mkdir /opt/odoo

WORKDIR /opt/odoo

COPY src/requirements.txt .

RUN pip3 install --no-cache-dir -r requirements.txt

RUN mkdir /opt/odoo/addons-ar \
    /opt/odoo/addons-ar/odoo-argentina \
    /opt/odoo/addons-ar/aeroo_reports

COPY src/addons-ar/odoo-argentina/requirements.txt addons-ar/odoo-argentina/

###
RUN apt-get install -y swig unzip libssl-dev 

RUN apt-get update

RUN apt-get install -y \
    build-essential \
    autoconf libtool \
    pkg-config \
    python-opengl \
    python-imaging \
    python-pyrex \
    python-pyside.qtopengl \
    idle-python2.7 \
    qt4-dev-tools \
    qt4-designer \
    libqtgui4 \
    libqtcore4 \
    libqt4-xml \
    libqt4-test \
    libqt4-script \
    libqt4-network \
    libqt4-dbus \
    python-qt4 \
    python-qt4-gl \
    libgle3 \
    python-dev

RUN apt-get install -y python-setuptools 

RUN easy_install greenlet

RUN easy_install gevent
###

RUN pip3 install --no-cache-dir -r addons-ar/odoo-argentina/requirements.txt

COPY src/addons-ar/aeroo_reports/requirements.txt addons-ar/aeroo_reports/

RUN pip3 install --no-cache-dir -r addons-ar/aeroo_reports/requirements.txt

# Instalar Java Runtime (necesario para Libreoffice)
RUN apt-get install default-jre -y

# Instalar herramientas y dependencias de aeroolib
RUN apt-get install git -y
RUN apt-get install python3-setuptools python3-uno -y
RUN apt-get install python3-lxml -y
RUN pip3 install jsonrpc2 daemonize

RUN mkdir /opt/aeroo
WORKDIR /opt/aeroo 
RUN git clone https://github.com/aeroo/aeroo_docs.git
RUN yes | python3 /opt/aeroo/aeroo_docs/aeroo-docs start -c /etc/aeroo-docs.conf
RUN ln -s /opt/aeroo/aeroo_docs/aeroo-docs /etc/init.d/aeroo-docs
RUN update-rc.d aeroo-docs defaults
RUN service aeroo-docs start
#RUN service aeroo-docs restart

RUN apt-get install libreoffice libreoffice-script-provider-python -y
RUN echo '#!/bin/sh' | tee /etc/init.d/office
RUN echo '/usr/bin/libreoffice --headless --accept="socket,host=localhost,port=8100,tcpNoDelay=1;urp;"&' | tee -a /etc/init.d/office
RUN chmod +x /etc/init.d/office
RUN update-rc.d office defaults
RUN /etc/init.d/office

RUN apt install unoconv -y

WORKDIR /opt/odoo

RUN sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'

RUN apt-get install -y wget

RUN wget -q https://www.postgresql.org/media/keys/ACCC4CF8.asc -O - | apt-key add -

RUN apt-get update -y
RUN apt-get upgrade -y

RUN apt-get install -y postgresql postgresql-contrib libpq-dev

RUN wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.1/wkhtmltox-0.12.1_linux-trusty-amd64.deb -O /tmp/wkhtml.deb \
   && dpkg -i /tmp/wkhtml.deb \
   && apt-get -f install

RUN pip3 install validate_email
RUN pip3 install phonenumbers
RUN pip3 install pysftp
