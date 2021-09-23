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

An  `initdb` folder should be created in you test resources. This folder will have the scripts sql which will execute when container is started.

**Default Properties Values:**
<docker-maven-plugin.version>0.37.0</docker-maven-plugin.version>
* `it.archimedesfw.docker.network` - archimedes
* `it.archimedesfw.postgresql.docker.image` - postgres:10-alpine
* `it.archimedesfw.postgresql.docker.alias` - archimedes-it-db
* `it.archimedesfw.postgresql.docker.internal_port` - 5432
* `it.archimedesfw.postgresql.db` - archimedes
* `it.archimedesfw.postgresql.user` - postgres
* `it.archimedesfw.postgresql.password` - verysecret
* `it.archimedesfw.postgresql.schema` - public
* `it.archimedesfw.postgresql.startupTimeout` - 20000
* `it.archimedesfw.postgresql.removeVolumesOnStop` - true
* `it.archimedesfw.postgresql.stopMode` - graceful
