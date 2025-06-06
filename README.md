# Plantuml to PNG CLI

## Motivation

Plantuml-to-png is a CLI utility designed to convert PlantUML files (.puml) to PNG format

When you store your `.puml` files in your repository, you need to do an extra step in order to generate the image in `.png` format using a Third party service.

Using this project, you could simplify this step.

![](./docs/screenshot.png)

## How to build in local?

```bash
./mvnw dependency:tree
./mvnw buildplan:list-phase
./mvnw license:third-party-report
jwebserver -p 8000 -d "$(pwd)/target/reports/"
./mvnw clean verify
./mvnw clean verify -DENABLE_INTEGRATION_TESTS=true
./mvnw clean verify surefire-report:report
./mvnw clean verify jacoco:report -Pjacoco
jwebserver -p 8001 -d "$(pwd)/target/site/jacoco"

./mvnw versions:display-property-updates
./mvnw versions:display-dependency-updates
./mvnw versions:display-plugin-updates
```

## How to test it?

```bash
./mvnw clean package
java -jar target/puml-to-png-0.5.0.jar --help
java -jar target/puml-to-png-0.5.0.jar --file ./docs/sample-diagram.puml
java -jar target/puml-to-png-0.5.0.jar --watch docs

# Update puml-to-png@jabrena only
jbang --fresh puml-to-png@jabrena
jbang catalog list jabrena

jbang puml-to-png@jabrena --help
jbang puml-to-png@jabrena --file ./docs/sample-diagram.puml
jbang puml-to-png@jabrena --watch docs
```

## References
- https://picocli.info/
- https://mvnrepository.com/artifact/net.sourceforge.plantuml/plantuml/1.2023.10
- https://graphviz.org/
- https://github.com/plantuml/plantuml
- https://plantuml.com/es/smetana02
- https://www.jbang.dev/appstore/
- ...
- https://github.com/jabrena/cursor-rules-agile
- https://github.com/jabrena/cursor-rules-java

Powered by [Cursor](https://www.cursor.com/)
