# Maven Wiremock Tile

This tile allows to start a [WireMock](http://wiremock.org/) Docker container for the integration tests.

Just add the following configuration to your `pom.xml` of your module you need it.

```xml
<plugin>
    <groupId>io.repaint.maven</groupId>
    <artifactId>tiles-maven-plugin</artifactId>
    <configuration>
        <applyBefore>io.archimedesfw.app:fake</applyBefore>
        <tiles>
            <tile>io.archimedesfw.maven.tiles:wiremock-tile:${last-version}</tile>
        </tiles>
    </configuration>
</plugin>
```

Your service will be automatically configured by the system properties: `it.archimedesfw.wiremock.host` and `it.archimedesfw.wiremock.port` with the dynamic port which the wiremock is listening.

The WireMock container will be registered in the `archimedes` network as `archimedes-it-wiremock`

A `wiremock-tile` folder should be created in you test resources. This folder should have another folder `mappings` with the wiremock files you want to use.

Those files would be placed into /home/wiremock folder inside the container as the image documentation explains.
