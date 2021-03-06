# Greensync

Tool for syncing [Greenhouse Harvest API](https://developers.greenhouse.io/harvest.html) and a MySQL database of your choice. It pulls new data every 15 minutes by default.

## Motivation

[Greenhouse](https://www.greenhouse.io/) allows you to access all your organisation data via their API. Unfortunately, for complex queries you'll have to chain multiple requests to relate entities, and take care of throttling and pagination by yourself. By syncing Greenhouse data into a relational database, you won't have to worry about the details, just query your database for the information you need.

## Run

Run the image

    docker run \
      -e DB_NAME="greensync" \
      -e DB_USER="greensync" \
      -e DB_PASS="pass" \
      -e DB_HOST="localhost" \
      -e GREENHOUSE_API_TOKEN="YOUR_TOKEN" \
      keyvanakbary/greensync

Additionally, you can pass the following environment variables

* `DB_PORT`, defaults to `3306`
* `CRON_SCHEDULE`, defaults to `*/15 * * * *` (every 15 minutes)

Run the tool along with a MySQL database via docker-compose

    GREENHOUSE_API_TOKEN="YOUR_TOKEN_HERE" docker-compose up

---

Run just the database

    docker-compose up mysql

Run the service via Mix

    GREENHOUSE_API_TOKEN="YOUR_TOKEN" mix run

Sync all via Mix task

    GREENHOUSE_API_TOKEN="YOUR_TOKEN" mix sync.all