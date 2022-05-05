```shell
mvn package
mvn clean package
sudo docker-compose up -d
sudo docker-compose logs -f
```

```
<plugin>
                <groupId>com.spotify</groupId>
                <artifactId>docker-maven-plugin</artifactId>
                <version>1.0.0</version>
                <executions>
                    <!--执行mvn package,即执行 mvn clean package docker:build-->
                    <execution>
                        <id>build-image</id>
                        <phase>package</phase>
                        <goals>
                            <goal>build</goal>
                        </goals>
                    </execution>
                </executions>

                <configuration>
                    <!-- 镜像名称 -->
                    <imageName>${project.artifactId}</imageName>
                    <!-- 指定标签 -->
                    <imageTags>
                        <imageTag>latest</imageTag>
                    </imageTags>
                    <!-- 基础镜像-->
                    <baseImage>openjdk:8-jdk-alpine</baseImage>

                    <!-- 切换到容器工作目录-->
                    <workdir>/ROOT</workdir>

                    <entryPoint>["java","-jar","${project.build.finalName}.jar"]</entryPoint>

                    <!-- 指定远程 Docker API地址  -->
                    <!--<dockerHost>http://121.196.99.215:10010</dockerHost>-->

                    <!-- 复制 jar包到docker容器指定目录-->
                    <resources>
                        <resource>
<!--                            <targetPath>/root/wise-java/dev</targetPath>-->
                            <targetPath>/root/wise-java-dev</targetPath>
                            <!-- 用于指定需要复制的根目录，${project.build.directory}表示target目录 -->
                            <directory>${project.build.directory}</directory>
                            <!-- 用于指定需要复制的文件，${project.build.finalName}.jar就是打包后的target目录下的jar包名称　-->
                            <include>${project.build.finalName}.jar</include>
                        </resource>
                    </resources>
                </configuration>
            </plugin>
```