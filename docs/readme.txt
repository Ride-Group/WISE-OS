# 1.修改项目配置文件 application.yml
   active: docker

# 2.先进JAVA项目根路径 maven打包
   mvn clean package


# 3.构建镜像__容器组（当你改变本地代码，也可重新构建镜像）
   docker-compose build

# 4.配置host

# jeecgboot
127.0.0.1   jeecg-boot-redis
127.0.0.1   jeecg-boot-mysql
127.0.0.1   jeecg-boot-system

10.2.100.2 jeecg-boot-redis
10.2.100.2 jeecg-boot-mysql
10.2.100.2 jeecg-boot-system

# 5.启动镜像__容器组（也可取代运行中的镜像）
   docker-compose up -d

docker-compose logs -f

jeecg-boot-system    | 2021-03-16 11:48:57.583 [main] WARN  o.s.b.w.s.c.AnnotationConfigServletWebServerApplicationContext:559 - Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'sysMessageTemplateServiceImpl': Unsatisfied dependency expressed through field 'baseMapper'; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'sysMessageTemplateMapper' defined in URL [jar:file:/jeecg-boot/jeecg-boot-module-system-2.4.2.jar!/BOOT-INF/classes!/org/jeecg/modules/message/mapper/SysMessageTemplateMapper.class]: Unsatisfied dependency expressed through bean property 'sqlSessionFactory'; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'sqlSessionFactory' defined in class path resource [com/baomidou/mybatisplus/autoconfigure/MybatisPlusAutoConfiguration.class]: Unsatisfied dependency expressed through method 'sqlSessionFactory' parameter 0; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'dataSource' defined in class path resource [com/alibaba/druid/spring/boot/autoconfigure/DruidDataSourceAutoConfigure.class]: Invocation of init method failed; nested exception is org.springframework.boot.autoconfigure.jdbc.DataSourceProperties$DataSourceBeanCreationException: Failed to determine a suitable driver class
jeecg-boot-system    | 2021-03-16 11:48:57.676 [main] INFO  org.apache.catalina.core.StandardService:173 - Stopping service [Tomcat]
jeecg-boot-system    | 2021-03-16 11:48:57.798 [main] INFO  o.s.b.a.l.ConditionEvaluationReportLoggingListener:136 -
jeecg-boot-system    |
jeecg-boot-system    | Error starting ApplicationContext. To display the conditions report re-run your application with 'debug' enabled.
jeecg-boot-system    | 2021-03-16 11:48:57.801 [main] ERROR o.s.b.diagnostics.LoggingFailureAnalysisReporter:40 -
jeecg-boot-system    |
jeecg-boot-system    | ***************************
jeecg-boot-system    | APPLICATION FAILED TO START
jeecg-boot-system    | ***************************
jeecg-boot-system    |
jeecg-boot-system    | Description:
jeecg-boot-system    |
jeecg-boot-system    | Failed to configure a DataSource: 'url' attribute is not specified and no embedded datasource could be configured.
jeecg-boot-system    |
jeecg-boot-system    | Reason: Failed to determine a suitable driver class
jeecg-boot-system    |
jeecg-boot-system    |
jeecg-boot-system    | Action:
jeecg-boot-system    |
jeecg-boot-system    | Consider the following:
jeecg-boot-system    |  If you want an embedded database (H2, HSQL or Derby), please put it on the classpath.
jeecg-boot-system    |  If you have database settings to be loaded from a particular profile you may need to activate it (no profiles are currently active).
jeecg-boot-system    |
jeecg-boot-system exited with code 1



eecg-boot-system    | 2021-03-16 15:27:24.564 [main] ERROR com.alibaba.druid.pool.DruidDataSource:927 - init datasource error, url: jdbc:mysql://127.0.0.1:3307/jeecg-boot?characterEncoding=UTF-8&useUnicode=true&useSSL=false&tinyInt1isBit=false&allowPublicKeyRetrieval=true&serverTimezone=Asia/Shanghai
jeecg-boot-system    | com.mysql.cj.jdbc.exceptions.CommunicationsException: Communications link failure
jeecg-boot-system    |
jeecg-boot-system    | The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
jeecg-boot-system    |  at com.mysql.cj.jdbc.exceptions.SQLError.createCommunicationsException(SQLError.java:174)
jeecg-boot-system    |  at com.mysql.cj.jdbc.exceptions.SQLExceptionsMapping.translateException(SQLExceptionsMapping.java:64)
jeecg-boot-system    |  at com.mysql.cj.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:836)
jeecg-boot-system    |  at com.mysql.cj.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:456)
jeecg-boot-system    |  at com.mysql.cj.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:246)
jeecg-boot-system    |  at com.mysql.cj.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:198)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterChainImpl.connection_connect(FilterChainImpl.java:156)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterAdapter.connection_connect(FilterAdapter.java:787)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterEventAdapter.connection_connect(FilterEventAdapter.java:38)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterChainImpl.connection_connect(FilterChainImpl.java:150)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterAdapter.connection_connect(FilterAdapter.java:787)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterChainImpl.connection_connect(FilterChainImpl.java:150)
jeecg-boot-system    |  at com.alibaba.druid.filter.stat.StatFilter.connection_connect(StatFilter.java:218)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterChainImpl.connection_connect(FilterChainImpl.java:150)
jeecg-boot-system    |  at com.alibaba.druid.pool.DruidAbstractDataSource.createPhysicalConnection(DruidAbstractDataSource.java:1646)
jeecg-boot-system    |  at com.alibaba.druid.pool.DruidAbstractDataSource.createPhysicalConnection(DruidAbstractDataSource.java:1710)
jeecg-boot-system    |  at com.alibaba.druid.pool.DruidDataSource.init(DruidDataSource.java:923)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.creator.DruidDataSourceCreator.createDataSource(DruidDataSourceCreator.java:158)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.creator.DataSourceCreator.createDruidDataSource(DataSourceCreator.java:174)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.creator.DataSourceCreator.createDataSource(DataSourceCreator.java:92)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.provider.AbstractDataSourceProvider.createDataSourceMap(AbstractDataSourceProvider.java:45)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.provider.YmlDynamicDataSourceProvider.loadDataSources(YmlDynamicDataSourceProvider.java:43)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.DynamicRoutingDataSource.afterPropertiesSet(DynamicRoutingDataSource.java:229)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1853)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1790)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:594)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:516)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:324)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:322)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
jeecg-boot-system    |  at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:276)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1307)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1227)
jeecg-boot-system    |  at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:884)
jeecg-boot-system    |  at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:788)
jeecg-boot-system    |  at org.springframework.beans.factory.support.ConstructorResolver.instantiateUsingFactoryMethod(ConstructorResolver.java:538)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.instantiateUsingFactoryMethod(AbstractAutowireCapableBeanFactory.java:1336)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1176)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:556)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:516)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:324)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:322)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
jeecg-boot-system    |  at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:276)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1307)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1227)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.autowireByType(AbstractAutowireCapableBeanFactory.java:1509)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1404)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:593)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:516)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:324)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:322)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
jeecg-boot-system    |  at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:276)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1307)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1227)
jeecg-boot-system    |  at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor$AutowiredFieldElement.inject(AutowiredAnnotationBeanPostProcessor.java:640)
jeecg-boot-system    |  at org.springframework.beans.factory.annotation.InjectionMetadata.inject(InjectionMetadata.java:130)
jeecg-boot-system    |  at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor.postProcessProperties(AutowiredAnnotationBeanPostProcessor.java:399)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1420)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:593)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:516)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:324)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:322)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:897)
jeecg-boot-system    |  at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:879)
jeecg-boot-system    |  at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:551)
jeecg-boot-system    |  at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:143)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:758)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:750)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:405)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.run(SpringApplication.java:315)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.run(SpringApplication.java:1237)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.run(SpringApplication.java:1226)
jeecg-boot-system    |  at org.jeecg.JeecgSystemApplication.main(JeecgSystemApplication.java:32)
jeecg-boot-system    |  at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
jeecg-boot-system    |  at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
jeecg-boot-system    |  at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
jeecg-boot-system    |  at java.lang.reflect.Method.invoke(Method.java:498)
jeecg-boot-system    |  at org.springframework.boot.loader.MainMethodRunner.run(MainMethodRunner.java:49)
jeecg-boot-system    |  at org.springframework.boot.loader.Launcher.launch(Launcher.java:107)
jeecg-boot-system    |  at org.springframework.boot.loader.Launcher.launch(Launcher.java:58)
jeecg-boot-system    |  at org.springframework.boot.loader.JarLauncher.main(JarLauncher.java:88)
jeecg-boot-system    | Caused by: com.mysql.cj.exceptions.CJCommunicationsException: Communications link failure
jeecg-boot-system    |
jeecg-boot-system    | The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
jeecg-boot-system    |  at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
jeecg-boot-system    |  at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
jeecg-boot-system    |  at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
jeecg-boot-system    |  at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
jeecg-boot-system    |  at com.mysql.cj.exceptions.ExceptionFactory.createException(ExceptionFactory.java:61)
jeecg-boot-system    |  at com.mysql.cj.exceptions.ExceptionFactory.createException(ExceptionFactory.java:105)
jeecg-boot-system    |  at com.mysql.cj.exceptions.ExceptionFactory.createException(ExceptionFactory.java:151)
jeecg-boot-system    |  at com.mysql.cj.exceptions.ExceptionFactory.createCommunicationsException(ExceptionFactory.java:167)
jeecg-boot-system    |  at com.mysql.cj.protocol.a.NativeSocketConnection.connect(NativeSocketConnection.java:89)
jeecg-boot-system    |  at com.mysql.cj.NativeSession.connect(NativeSession.java:144)
jeecg-boot-system    |  at com.mysql.cj.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:956)
jeecg-boot-system    |  at com.mysql.cj.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:826)
jeecg-boot-system    |  ... 85 common frames omitted
jeecg-boot-system    | Caused by: java.net.ConnectException: Connection refused (Connection refused)
jeecg-boot-system    |  at java.net.PlainSocketImpl.socketConnect(Native Method)
jeecg-boot-system    |  at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:350)
jeecg-boot-system    |  at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:206)
jeecg-boot-system    |  at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:188)
jeecg-boot-system    |  at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:392)
jeecg-boot-system    |  at java.net.Socket.connect(Socket.java:589)
jeecg-boot-system    |  at com.mysql.cj.protocol.StandardSocketFactory.connect(StandardSocketFactory.java:155)
jeecg-boot-system    |  at com.mysql.cj.protocol.a.NativeSocketConnection.connect(NativeSocketConnection.java:63)
jeecg-boot-system    |  ... 88 common frames omitted
jeecg-boot-system    | 2021-03-16 15:27:24.570 [main] ERROR com.alibaba.druid.pool.DruidDataSource:969 - {dataSource-1} init error
jeecg-boot-system    | com.mysql.cj.jdbc.exceptions.CommunicationsException: Communications link failure
jeecg-boot-system    |
jeecg-boot-system    | The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
jeecg-boot-system    |  at com.mysql.cj.jdbc.exceptions.SQLError.createCommunicationsException(SQLError.java:174)
jeecg-boot-system    |  at com.mysql.cj.jdbc.exceptions.SQLExceptionsMapping.translateException(SQLExceptionsMapping.java:64)
jeecg-boot-system    |  at com.mysql.cj.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:836)
jeecg-boot-system    |  at com.mysql.cj.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:456)
jeecg-boot-system    |  at com.mysql.cj.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:246)
jeecg-boot-system    |  at com.mysql.cj.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:198)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterChainImpl.connection_connect(FilterChainImpl.java:156)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterAdapter.connection_connect(FilterAdapter.java:787)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterEventAdapter.connection_connect(FilterEventAdapter.java:38)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterChainImpl.connection_connect(FilterChainImpl.java:150)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterAdapter.connection_connect(FilterAdapter.java:787)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterChainImpl.connection_connect(FilterChainImpl.java:150)
jeecg-boot-system    |  at com.alibaba.druid.filter.stat.StatFilter.connection_connect(StatFilter.java:218)
jeecg-boot-system    |  at com.alibaba.druid.filter.FilterChainImpl.connection_connect(FilterChainImpl.java:150)
jeecg-boot-system    |  at com.alibaba.druid.pool.DruidAbstractDataSource.createPhysicalConnection(DruidAbstractDataSource.java:1646)
jeecg-boot-system    |  at com.alibaba.druid.pool.DruidAbstractDataSource.createPhysicalConnection(DruidAbstractDataSource.java:1710)
jeecg-boot-system    |  at com.alibaba.druid.pool.DruidDataSource.init(DruidDataSource.java:923)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.creator.DruidDataSourceCreator.createDataSource(DruidDataSourceCreator.java:158)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.creator.DataSourceCreator.createDruidDataSource(DataSourceCreator.java:174)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.creator.DataSourceCreator.createDataSource(DataSourceCreator.java:92)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.provider.AbstractDataSourceProvider.createDataSourceMap(AbstractDataSourceProvider.java:45)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.provider.YmlDynamicDataSourceProvider.loadDataSources(YmlDynamicDataSourceProvider.java:43)
jeecg-boot-system    |  at com.baomidou.dynamic.datasource.DynamicRoutingDataSource.afterPropertiesSet(DynamicRoutingDataSource.java:229)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1853)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1790)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:594)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:516)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:324)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:322)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
jeecg-boot-system    |  at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:276)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1307)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1227)
jeecg-boot-system    |  at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:884)
jeecg-boot-system    |  at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:788)
jeecg-boot-system    |  at org.springframework.beans.factory.support.ConstructorResolver.instantiateUsingFactoryMethod(ConstructorResolver.java:538)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.instantiateUsingFactoryMethod(AbstractAutowireCapableBeanFactory.java:1336)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1176)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:556)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:516)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:324)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:322)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
jeecg-boot-system    |  at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:276)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1307)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1227)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.autowireByType(AbstractAutowireCapableBeanFactory.java:1509)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1404)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:593)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:516)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:324)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:322)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
jeecg-boot-system    |  at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:276)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1307)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1227)
jeecg-boot-system    |  at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor$AutowiredFieldElement.inject(AutowiredAnnotationBeanPostProcessor.java:640)
jeecg-boot-system    |  at org.springframework.beans.factory.annotation.InjectionMetadata.inject(InjectionMetadata.java:130)
jeecg-boot-system    |  at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor.postProcessProperties(AutowiredAnnotationBeanPostProcessor.java:399)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1420)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:593)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:516)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:324)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:322)
jeecg-boot-system    |  at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
jeecg-boot-system    |  at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:897)
jeecg-boot-system    |  at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:879)
jeecg-boot-system    |  at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:551)
jeecg-boot-system    |  at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:143)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:758)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:750)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:405)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.run(SpringApplication.java:315)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.run(SpringApplication.java:1237)
jeecg-boot-system    |  at org.springframework.boot.SpringApplication.run(SpringApplication.java:1226)
jeecg-boot-system    |  at org.jeecg.JeecgSystemApplication.main(JeecgSystemApplication.java:32)
jeecg-boot-system    |  at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
jeecg-boot-system    |  at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
jeecg-boot-system    |  at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
jeecg-boot-system    |  at java.lang.reflect.Method.invoke(Method.java:498)
jeecg-boot-system    |  at org.springframework.boot.loader.MainMethodRunner.run(MainMethodRunner.java:49)
jeecg-boot-system    |  at org.springframework.boot.loader.Launcher.launch(Launcher.java:107)
jeecg-boot-system    |  at org.springframework.boot.loader.Launcher.launch(Launcher.java:58)
jeecg-boot-system    |  at org.springframework.boot.loader.JarLauncher.main(JarLauncher.java:88)
jeecg-boot-system    | Caused by: com.mysql.cj.exceptions.CJCommunicationsException: Communications link failure
jeecg-boot-system    |
jeecg-boot-system    | The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
jeecg-boot-system    |  at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
jeecg-boot-system    |  at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
jeecg-boot-system    |  at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
jeecg-boot-system    |  at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
jeecg-boot-system    |  at com.mysql.cj.exceptions.ExceptionFactory.createException(ExceptionFactory.java:61)
jeecg-boot-system    |  at com.mysql.cj.exceptions.ExceptionFactory.createException(ExceptionFactory.java:105)
jeecg-boot-system    |  at com.mysql.cj.exceptions.ExceptionFactory.createException(ExceptionFactory.java:151)
jeecg-boot-system    |  at com.mysql.cj.exceptions.ExceptionFactory.createCommunicationsException(ExceptionFactory.java:167)
jeecg-boot-system    |  at com.mysql.cj.protocol.a.NativeSocketConnection.connect(NativeSocketConnection.java:89)
jeecg-boot-system    |  at com.mysql.cj.NativeSession.connect(NativeSession.java:144)
jeecg-boot-system    |  at com.mysql.cj.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:956)
jeecg-boot-system    |  at com.mysql.cj.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:826)
jeecg-boot-system    |  ... 85 common frames omitted
jeecg-boot-system    | Caused by: java.net.ConnectException: Connection refused (Connection refused)
jeecg-boot-system    |  at java.net.PlainSocketImpl.socketConnect(Native Method)
jeecg-boot-system    |  at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:350)
jeecg-boot-system    |  at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:206)
jeecg-boot-system    |  at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:188)
jeecg-boot-system    |  at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:392)
jeecg-boot-system    |  at java.net.Socket.connect(Socket.java:589)
jeecg-boot-system    |  at com.mysql.cj.protocol.StandardSocketFactory.connect(StandardSocketFactory.java:155)
jeecg-boot-system    |  at com.mysql.cj.protocol.a.NativeSocketConnection.connect(NativeSocketConnection.java:63)
jeecg-boot-system    |  ... 88 common frames omitted
jeecg-boot-system    | 2021-03-16 15:27:24.573 [main] INFO  com.alibaba.druid.pool.DruidDataSource:994 - {dataSource-1,master} inited
jeecg-boot-system    | 2021-03-16 15:27:24.575 [main] WARN  o.s.b.w.s.c.AnnotationConfigServletWebServerApplicationContext:559 - Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'sysMessageTemplateServiceImpl': Unsatisfied dependency expressed through field 'baseMapper'; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'sysMessageTemplateMapper' defined in URL [jar:file:/jeecg-boot/jeecg-boot-module-system-2.4.2.jar!/BOOT-INF/classes!/org/jeecg/modules/message/mapper/SysMessageTemplateMapper.class]: Unsatisfied dependency expressed through bean property 'sqlSessionFactory'; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'sqlSessionFactory' defined in class path resource [com/baomidou/mybatisplus/autoconfigure/MybatisPlusAutoConfiguration.class]: Unsatisfied dependency expressed through method 'sqlSessionFactory' parameter 0; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'dataSource' defined in class path resource [com/baomidou/dynamic/datasource/spring/boot/autoconfigure/DynamicDataSourceAutoConfiguration.class]: Invocation of init method failed; nested exception is com.baomidou.dynamic.datasource.exception.ErrorCreateDataSourceException: druid create error

jeecg-boot-system    | ----------------------------------------------------------
jeecg-boot-system    |  Application Jeecg-Boot is running! Access URLs:
jeecg-boot-system    |  Local:          http://localhost:8080/jeecg-boot/
jeecg-boot-system    |  External:       http://172.22.0.4:8080/jeecg-boot/
jeecg-boot-system    |  Swagger文档:    http://172.22.0.4:8080/jeecg-boot/doc.html
jeecg-boot-system    | ----------------------------------------------------------
