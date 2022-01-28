docker -v
docker run hello-world
vim Dockerfile
vim pipeline.py
docker build -t py39:pandas .
docker run -it py39:pandas 2022-01-27

docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v $(pwd)/nytaxi_data:/var/lib/postgresql/data \
  -p 5432:5432 \
  postgres:13

sudo apt-get install python3-psycopg2
sudo apt install pgcli
pgcli -hlocalhost -uroot -dny_taxi

pip install jupyter
pip install pandas
jupyter notebook

https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page
Yellow Taxi Trip Records (CSV) (Jan 2021)

head -n 250 yellow_tripdata_2021-01.csv > yellow_head.csv
wc -l yellow_tripdata_2021-01.csv

https://www1.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf
https://s3.amazonaws.com/nyc-tlc/misc/taxi+_zone_lookup.csv

pip install sqlalchemy

docker run -it \
  -e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
  -e PGADMIN_DEFAULT_PASSWORD="root" \
  -p 8081:80 \
  --network=pg-network \
  --name pgadmin \
  dpage/pgadmin4

docker network create pg-network

docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v $(pwd)/nytaxi_data:/var/lib/postgresql/data \
  -p 5432:5432 \
  --network=pg-network \
  --name pgdb \
  postgres:13
