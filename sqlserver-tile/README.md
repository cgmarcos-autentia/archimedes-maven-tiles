# Maven SQL Server Tile

Just add the following configuration to your `pom.xml` of your module you need it.

```xml
<plugin>
    <groupId>io.repaint.maven</groupId>
    <artifactId>tiles-maven-plugin</artifactId>
    <configuration>
        <applyBefore>io.archimedesfw.app:fake</applyBefore>
        <tiles>
            <tile>io.archimedesfw.maven.tiles:sqlserver-tile:${last-version}</tile>
        </tiles>
    </configuration>
</plugin>
```

Your service will be automatically configured by the system properties: `it.archimedesfw.sqlserver.host` and `it.archimedesfw.sqlserver.port` with the dynamic port which the database is listening.

The PostgreSQL container will be registered in the `archimedes` network as `archimedes-it-db`

An  `initdb` folder should be created in you test resources. This folder will have the scripts sql which will execute when container is started.

**Default Properties Values:**
<docker-maven-plugin.version>0.37.0</docker-maven-plugin.version>

* `it.archimedesfw.docker.network` - archimedes
* `it.archimedesfw.sqlserver.docker.image` - mcr.microsoft.com/mssql/server:2017-GA-ubuntusqlserver.docker.image` - 
* `it.archimedesfw.sqlserver.docker.alias` - archimedes-sqlserver-db
* `it.archimedesfw.sqlserver.docker.internal_port` - 1433
* `it.archimedesfw.sqlserver.user` - SA
* `it.archimedesfw.sqlserver.password` - verysecret
* `it.archimedesfw.sqlserver.pid` - Enterprise 
* `it.archimedesfw.sqlserver.startupTimeout` - 45000
* `it.archimedesfw.sqlserver.stopMode` - graceful
* `it.archimedesfw.sqlserver.removeVolumesOnStop` - true