---
title: How to deploy database to Azure?
---
# How to deploy database to Azure?

1. From your Azure portal, click 'create a resource'.
2. Search for '**Azure Database for PostgreSQL'.** Then hit 'create'.
3. Fill out project details, then submit.
4. On the left bar, click 'Databases', then add one.
5. Go to your local repository, and add postgres dependency to pom.
6. From 'application.yml', add configuration to align to database credentials.

```
debug: true
spring:
  sql:
    init:
      platform: postgresql
      mode: never
    output:
      ansi:
        enabled: always
  datasource:
    url: jdbc:postgresql://[your-app-name].postgres.database.azure.com:5432/[name-of-your-database]
    username: [add-user]
    password: [add-password]
  jpa:
    show-sql: true
    defer-datasource-initialization: true
    hibernate.ddl-auto: update
logging:
  level:
    org:
      springframework:
        boot:
          autoconfigure: ERROR

Note: Copy the url from Azure, and add the name of your database from the last '/'.
```

7. Launch DBeaber. Click 'postgres' > 'Databases' > \[name-of-database\] > 'Schemas' > 'public' > 'Tables'

**To add data to table for testing connection with backend:**

1. Click postgres > \[created-database-name\] > Schemas > public > Tables > \[name-of-entity-in-backend\].
2. Write click on \[entity-name\] > Generate SQL > \[pick-from-options\].
