FROM python:3.8-slim

#this is a really simple image that does the job with minimal requirements. 
#I included both the english and non-english DB so they can be accessed from the same container and page, but if you want to only use one of them just comment/delete the relevant COPY command and edit the entry CMD

RUN pip install datasette datasette-json-html datasette-pretty-json
RUN mkdir /dataset
WORKDIR /dataset

COPY index.db /dataset/index.db
COPY index-eng.db /dataset/index-eng.db
COPY metadata.json /dataset/metadata.json

EXPOSE 8001

CMD datasette serve index-eng.db index.db -h 0.0.0.0 --config sql_time_limit_ms:10000 --config allow_download:off --config max_returned_rows:2000  --config num_sql_threads:10 --metadata metadata.json
