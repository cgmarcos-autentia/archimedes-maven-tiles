# Maven PostgreSQL Tile

This tile allows to start a PostgreSQL Docker container for the integration tests.

Just add the following configuration to your `pom.xml` of your module you need it.

```xml
<plugin>
    <groupId>io.repaint.maven</groupId>
    <artifactId>tiles-maven-plugin</artifactId>
    <configuration>
        <applyBefore>io.archimedesfw.app:fake</applyBefore>
        <tiles>
            <tile>io.archimedesfw.maven.tiles:postgresql-tile:${last-version}</tile>
        </tiles>
    </configuration>
</plugin>
```

Your service will be automatically configured by the system properties: `it.archimedesfw.postgresql.host` and `it.archimedesfw.postgresql.port` with the dynamic port which the database is listening.

The PostgreSQL container will be registered in the `archimedes` network as `archimedes-it-db`

A `initdb` folder should be created in you test resources. This folder will have the scripts sql which will execute when container is started.
