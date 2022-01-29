# Docker Commands 

### DB BackUp
```docker exec -t containerName pg_dump -U postgres  dbname > dump_`date +%d-%m-%Y"_"%H_%M_%S`.sql```

### DB Restore
`cat your_dump.sql | docker exec -i  containerName psql -U postgres`

### Start Postgres Container
``` docker run --name docker-pg -p 5433:5432 -e POSTGRES_PASSWORD=password -d postgres:13-alpine ```

### Start RabbitMQ Container
``` docker run --name docker-mq -p 5673:5672 -p 15673:15672 -e RABBITMQ_DEFAULT_USER=admin  -e RABBITMQ_DEFAULT_PASS=password -d rabbitmq:3.8-management```