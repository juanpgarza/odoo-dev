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

RUN wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.bionic_amd64.deb

RUN apt install -y ./wkhtmltox_0.12.5-1.bionic_amd64.deb

#RUN wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.1/wkhtmltox-0.12.1_linux-trusty-amd64.deb -O /tmp/wkhtml.deb

#RUN dpkg -i /tmp/wkhtml.deb; exit 0

#RUN apt-get -f install -y

RUN apt-get update

RUN apt-get install -y postgresql-client

RUN pip3 install polib

RUN pip3 install Werkzeug==0.14.1

RUN apt-get update \
    && apt-get upgrade -y
	
RUN apt-get install git -y

RUN apt-get install python3-openssl
# RUN pip3 install pyOpenSSL

RUN apt update && apt install swig -y

RUN pip3 install M2Crypto

RUN pip3 install httplib2>=0.7

RUN pip3 install git+https://github.com/pysimplesoap/pysimplesoap@stable_py3k

RUN pip3 install git+https://github.com/ingadhoc/pyafipws@py3k

# RUN pip3 install git+https://github.com/OCA/openupgradelib/@master

WORKDIR /opt/odoo

