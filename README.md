**Assembly descriptor to share common packaging across projects**

Package together war files with other distribution files required for remote deployment.

*Example pom*
```
<build>
    <finalName>${project.artifactId}</finalName>
    <plugins>
        <plugin>
            <groupId>com.ariht</groupId>
            <artifactId>config-generation-maven-plugin</artifactId>
            <executions>
                <execution>
                    <goals>
                        <goal>generate</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
        <plugin>
            <artifactId>maven-assembly-plugin</artifactId>
            <version>2.4</version>
            <dependencies>
                <dependency>
                    <groupId>com.ariht</groupId>
                    <artifactId>maven-assembly-descriptor</artifactId>
                    <version>0.9.2</version>
                </dependency>
            </dependencies>
            <executions>
                <execution>
                    <id>make-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>assembly-war-distribution</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```
