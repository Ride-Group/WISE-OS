```shell
git pull
cd WISE-Fork/jeecg-boot
mvn package
mvn clean package

sudo docker-compose build
sudo docker-compose up -d
sudo docker-compose down

sudo docker-compose up jeecg-boot-system
sudo docker-compose up -d jeecg-boot-system
sudo docker-compose stop jeecg-boot-system

sudo docker-compose logs -f

mysql -h127.0.0.1 -uroot -p -P3308
root

use jeecg-boot
show tables;

mysql -h127.0.0.1 -uroot -p -P3308 jeecg-boot < ../../sql/wised.sql
root

http://49.232.6.131:8088/wise-dev
http://49.232.6.131:8088/wise-dev/doc.html
```

```shell
https://github.com/hexojs/hexo/
```

```
<!-- 排除依赖包 -->
                    <layout>ZIP</layout>
                    <includes>
                        <include>
                            <groupId>org.jeecgframework.boot</groupId>
                            <artifactId>jeecg-boot-module-bbs</artifactId>
                        </include>
                    </includes>
                    <!-- 排除依赖 -->
                    
<!-- 排除依赖包 -->
                <executions>
                    <execution>
                        <goals>
                            <goal>repackage</goal>
                        </goals>
                    </execution>
                </executions>
                
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