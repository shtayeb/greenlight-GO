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

## Run the server
```shell
go run ./cmd/api/ -smtp-username=<username> -smtp-password=<password>
```

## Flags
```shell
❯ go run ./cmd/api/ -help
Usage of /tmp/go-build1036895751/b001/exe/api:
  -db-dsn string
        PostgreSQL DSN (default "postgres://go_user:go_1234@localhost/greenlight")
  -db-max-idle-conns int
        PostgreSQL max idle connections (default 25)
  -db-max-idle-time string
        PostgreSQL max connection idle time (default "15m")
  -db-max-open-conns int
        PostgreSQL max open connections (default 25)
  -env string
        Environment (development|staging|production) (default "development")
  -limiter-burst int
        Rate limiter maximum burst (default 4)
  -limiter-enabled
        Enable rate limiter (default true)
  -limiter-rps float
        Rate limiter maximum requests per second (default 2)
  -port int
        API server port (default 4000)
  -smtp-host string
        SMTP host (default "smtp.mailtrap.io")
  -smtp-password string
        SMTP password
  -smtp-port int
        SMTP port (default 25)
  -smtp-sender string
        SMTP sender (default "no-reply@shtb.dev")
  -smtp-username string
        SMTP username
```

## Others
To test requests
```shell
go install github.com/rakyll/hey@master
```
