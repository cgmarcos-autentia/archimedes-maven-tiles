# Maven Micronaut App Launcher Tile

This tile is a extension of allows `io.archimedesfw.maven.tiles:app-launcher-tile` tile adding system properties to configure automatically a Micronaut application.

Just add the following configuration to your `pom.xml` of your module you need it.

```xml
<plugin>
    <groupId>io.repaint.maven</groupId>
    <artifactId>tiles-maven-plugin</artifactId>
    <configuration>
        <applyBefore>io.archimedesfw.app:fake</applyBefore>
        <tiles>
            <tile>io.archimedesfw.maven.tiles:micronaut-app-launcher-tile:${last-version}</tile>
        </tiles>
    </configuration>
</plugin>
```

By default, Micronaut application is running with:
- Environment with value `test`.
- Enabled the JWT security using `jwks.json` file stored in `src/test/resources/app-launcher-tile/security` folder.

You can disable some security settings using the next maven properties:
- `it.archimedesfw.micronaut.security.enabled`: enable/disable Micronaut security.
- `it.archimedesfw.micronaut.security.jwt.enabled`: enable/disable JWT security.
- `it.archimedesfw.micronaut.security.jwt.bearer.enabled`: enable/disable Bearer HTTP Header security.
