## Clone the repo
```shell
git clone https://github.com/shtayeb/greenlight-GO
```

## Postgres Database

```shell
psql -U postgres
```
Create a postgres database
```sql
CREATE DATABASE go_user_db OWNER go_user;
```

## Set DB DSN env variable
```shell
GREENLIGHT_DB_DSN="postgres://go_user:go_1234@localhost/snippetbox"
```

## Run migrations
install go migrate tool
```shell
curl -L https://github.com/golang-migrate/migrate/releases/download/v4.14.1/migrate.linux-amd64.tar.gz | tar xvz

mv migrate.linux-amd64 $GOPATH/bin/migrate
```

use GO migrate tool to apply migrations
```shell
migrate -path=./migrations -database=$GREENLIGHT_DB_DSN up
```
