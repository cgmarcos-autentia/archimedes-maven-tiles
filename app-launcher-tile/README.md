# Maven App Launcher Tile

This tile allows to start a App Docker container for the acceptance tests.

Just add the following configuration to your `pom.xml` of your module you need it.

```xml
<plugin>
    <groupId>io.repaint.maven</groupId>
    <artifactId>tiles-maven-plugin</artifactId>
    <configuration>
        <applyBefore>io.archimedesfw.app:fake</applyBefore>
        <tiles>
            <tile>io.archimedesfw.maven.tiles:app-launcher-tile:${last-version}</tile>
        </tiles>
    </configuration>
</plugin>
```

Your service will be automatically configured by the system properties `it.archimedesfw.app.endpoint`, `it.archimedesfw.app.host` and `it.archimedes.app.port` with the dynamic port which the application is listening.

The App container will be registered in the `archimedesfw` network as `archimedesfw-it-app`.

A resource `.env` should be added to test resources in `app-launcher-tile` folder. This file will have all env properties that you service need it.

The tile has been configured to use `@` character like delimiter for defining variables which will be substituted for maven properties. For example, it is useful when you need to configure the database connectivity of your application which has been configured using `postgresql-tile`.

**Default Properties values:**
* `docker-maven-plugin.version` - 0.37.0
* `it.archimedesfw.docker.network` - archimedes
* `it.archimedesfw.app.docker.image` - local/${project.parent.artifactId}:${docker.tag}
* `it.archimedesfw.app.docker.internal_port` - 8080
* `it.archimedesfw.app.docker.alias` - archimedes-it-app
* `it.archimedesfw.app.removeVolumesOnStop` - true
* `it.archimedesfw.app.stopMode` - graceful [graceful, kill]