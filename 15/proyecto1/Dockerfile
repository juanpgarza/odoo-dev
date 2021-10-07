FROM ubuntu:20.04
LABEL Creator: "juanpgarza"

RUN apt-get update \
    && apt-get upgrade -y

#3
RUN apt-get install -y python3-pip

RUN apt-get install python-dev python3-dev libxml2-dev libxslt1-dev zlib1g-dev libsasl2-dev \
                    libldap2-dev build-essential libssl-dev libffi-dev libmysqlclient-dev \
                    libjpeg-dev libpq-dev libjpeg8-dev liblcms2-dev libblas-dev libatlas-base-dev


RUN apt-get install -y npm
RUN ln -s /usr/bin/nodejs /usr/bin/node
RUN npm install -g less less-plugin-clean-css
RUN apt-get install -y node-less

# 4 Postgres

# 5
RUN adduser --system --home=/opt/odoo --group odoo

# 6 - Clonar repos


# 7 - 
WORKDIR /opt/odoo

COPY src/requirements.txt .

RUN pip3 install -r requirements.txt

# 8
RUN wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.bionic_amd64.deb
RUN dpkg -i wkhtmltox_0.12.5-1.bionic_amd64.deb
RUN apt install -f

