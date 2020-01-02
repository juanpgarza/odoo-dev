FROM ubuntu:18.04
LABEL Creator: "juanpgarza"

RUN apt-get update \
    && apt-get upgrade -y

RUN apt-get install -y \
    openssh-server fail2ban

#RUN adduser --system --home=/opt/odoo --group odoo
RUN adduser --disabled-password --gecos "Odoo" odoo

RUN apt-get install -y \
    python3-pip

RUN apt-get update \
    && \
    apt-get install -y npm \
    && \
    npm install -g less less-plugin-clean-css \
    && \
	apt-get install -y node-less
	
RUN apt-get update \
    && \
    apt-get install -y \
    nano

#RUN mkdir /opt/odoo

#WORKDIR /opt/odoo

#COPY src/requirements.txt .

#RUN pip3 install --no-cache-dir -r requirements.txt
RUN apt-get update \
    && \
    apt-get install -y \
    python3-dev \
    python3-pip \
    libxml2-dev \
    libxslt1-dev \
    libevent-dev \
    libsasl2-dev \
    libldap2-dev \
    libpq-dev \
    libjpeg-dev \
    poppler-utils \
    node-less \
    node-clean-css

RUN apt-get install -y wget gdebi-core

RUN pip3 install Babel decorator docutils ebaysdk feedparser gevent greenlet html2text Jinja2 lxml Mako MarkupSafe mock num2words ofxparse passlib Pillow psutil psycogreen psycopg2 pydot pyparsing PyPDF2 pyserial python-dateutil python-openid pytz pyusb PyYAML qrcode reportlab requests six suds-jurko vatnumber vobject Werkzeug XlsxWriter xlwt xlrd gdata

RUN pip3 install libsass==0.12.3

#RUN apt-get -f install -y

RUN apt install python3-daemonize

RUN pip3 install phonenumbers

RUN apt-get install git -y

RUN pip3 install pyOpenSSL M2Crypto httplib2>=0.7 git+https://github.com/pysimplesoap/pysimplesoap@stable_py3k git+https://github.com/ingadhoc/pyafipws@py3k

RUN pip3 install git+https://github.com/edgewall/genshi@stable/0.7.x git+https://github.com/adhoc-dev/aeroolib@master-fix-ods git+https://github.com/aeroo/currency2text.git

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

RUN wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.bionic_amd64.deb

RUN apt install -y ./wkhtmltox_0.12.5-1.bionic_amd64.deb

RUN apt-get update

RUN apt-get install -y postgresql-client
