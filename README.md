## Set DB DSN env variable
```shell
GREENLIGHT_DB_DSN="postgres://go_user:go_1234@localhost/snippetbox"
```

## Run migrations
use GO migrate tool
```shell
migrate -path=./migrations -database=$GREENLIGHT_DB_DSN up
```
