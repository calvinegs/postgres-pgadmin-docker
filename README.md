# 使用 Docker 來執行 PostgreSQL 和 pgAdmin

## 執行 docker compose

在與 docker-compose.yml 的相同目錄中執行 `docker compose up`，執行完成後再另一個 terminal 中使用 $ docker ps 指令查看容器啟動狀況

```bash
$ docker compose up

# ...
pg_server  | 2022-06-01 13:39:11.333 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
pg_server  | 2022-06-01 13:39:11.333 UTC [1] LOG:  listening on IPv6 address "::", port 5432
pg_server  | 2022-06-01 13:39:11.335 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
pg_server  | 2022-06-01 13:39:11.340 UTC [64] LOG:  database system was shut down at 2022-06-01 13:39:11 UTC
pg_server  | 2022-06-01 13:39:11.346 UTC [1] LOG:  database system is ready to accept connections
pg_admin   | NOTE: Configuring authentication for DESKTOP mode.
pg_admin   | ----------
pg_admin   | Loading servers with:
pg_admin   | User: pgadmin4@pgadmin.org
pg_admin   | SQLite pgAdmin config: /var/lib/pgadmin/pgadmin4.db
pg_admin   | ----------
pg_admin   | Added 0 Server Group(s) and 1 Server(s).
pg_admin   | [2022-06-01 13:39:48 +0000] [1] [INFO] Starting gunicorn 20.1.0
pg_admin   | [2022-06-01 13:39:48 +0000] [1] [INFO] Listening at: http://[::]:80 (1)
pg_admin   | [2022-06-01 13:39:48 +0000] [1] [INFO] Using worker: gthread
pg_admin   | [2022-06-01 13:39:48 +0000] [91] [INFO] Booting worker with pid: 91
```

```bash
$ docker ps
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS                    PORTS                                            NAMES
11bb5b91463c   dpage/pgadmin4:6.9   "/entrypoint.sh"         17 seconds ago   Up 5 seconds              443/tcp, 0.0.0.0:5431->80/tcp, :::5431->80/tcp   pg_admin
1dbca769db67   postgres:14.3        "docker-entrypoint.s…"   17 seconds ago   Up 16 seconds (healthy)   0.0.0.0:5432->5432/tcp, :::5432->5432/tcp        pg_serve
```

## 使用 PgAdmin 連結到 Postgres DB

開啟瀏覽器輸入 http://localhost:5431 可連結到 postgras 資料庫。更詳細資訊 [打開][pgadmin]

[pgadmin]: https://www.pgadmin.org/docs/