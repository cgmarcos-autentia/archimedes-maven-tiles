This tile is a extension of `io.archimedesfw.maven.tiles:postgresql-tile` tile adding system properties to configure automatically Micronaut.

Just add the following configuration to your `pom.xml` of your module you need it.

```xml
<plugin>
    <groupId>io.repaint.maven</groupId>
    <artifactId>tiles-maven-plugin</artifactId>
    <configuration>
        <applyBefore>io.archimedesfw.app:fake</applyBefore>
        <tiles>
            <tile>io.archimedesfw.maven.tiles:micronaut-postgresql-tile:${last-version}</tile>
        </tiles>
    </configuration>
</plugin>
```

Your service will be automatically configured by the system properties: `datasources.default.url`, `datasources.default.username`, `datasources.default.password` and  `datasources.default.hikari.schema` in order to establish the connection using Micronaut.

If your datasource is not named default you can configure the property `it.archimedesfw.postgresql.datasource` to specify your datasource name.

Microanut Flyway scripts locations property is configured too using  `classpath:db.migration` and `classpath:db.sampledata` locations. You could change these locations with property `it.archimedesfw.flyway.locations`.

**Default Properties Values:**
* `it.archimedesfw.postgresql.datasource`- default
* `it.archimedesfw.postgresql.flyway.locations` - classpath:db.migration,classpath:db.sampledata


