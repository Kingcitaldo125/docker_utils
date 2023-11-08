FROM python:3.10.8

WORKDIR /angr_temp/

COPY requirements.txt .

RUN pip install -r requirements.txt

WORKDIR /

RUN rm -rf angr_temp/

CMD [ "bash" ]
