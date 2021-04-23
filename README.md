# Microservice Environment


- API gateway and service registry using Eureka and Zuul.
- Use Docker to start services.

![image](https://user-images.githubusercontent.com/49173138/115921903-c501ef80-a441-11eb-987a-2ab4e4e75e0d.png)

### Structure


- The API Gateway - Each of our services will have its own URL. A client may require data from each of those, and managing several URLs can be extremely cumbersome. An API gateway will allow us to create a single entry-point for any client to consume.
- The Service Registry - Our API gateway needs to know where our services live so that it can shuttle data back and forth. The Service Registry will keep a live "database" of each of our services, along with its address. As new services spin up, they will automatically register themselves in this database, and therefore automatically expose themselves through our central API Gateway URL.
- Services - Each of our services will be its own, fully-functioning application. They will look like mini versions of a monolithic app. The only thing we will need to add to our little MVC services is the ability to register with the Service Registry on startup.

### Endpoints

- localhost:8761 should have our API-GATEWAY and USERS apps registered
- localhost:8081/users/ should return "some users"

Access to postgres:

- localhost:5432
- Username: postgres (as a default)
- Password: nE5kMc7JCGNqwDQM (as a default)

Access to PgAdmin:

- URL: http://localhost:5050
- Username: pgadmin4@pgadmin.org (as a default)
- Password: admin (as a default)

To add a new server in PgAdmin:

- Host name/address postgres_db
- Port 5432
- Username as POSTGRES_USER, by default: postgres
- Password as POSTGRES_PASSWORD, by default nE5kMc7JCGNqwDQM

### Seed DB

```touch src/main/resources/db/migration/afterMigrate.sql```

```INSERT INTO users(user_name, first_name, last_name)
VALUES ('quinto', 'timothy', 'quinto'),
('darkness', 'charlie', 'murphy'),
('hilldawg', 'hillary', 'clinton'),
('onionfan', 'ser', 'davos'),
('1337codr', 'mad', 'hax'),
('badstash', 'charlie', 'chaplin');
```

