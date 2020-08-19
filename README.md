# 出租房管理系统
ssm开源的出租管理项目，后期会持续更新框架技术。
## 项目简介
出租管理系统 housesSys

本出租管理项目为个人，springboot+zookeper分布式高集群项目，实现租房出租管理（项目持续开发.....）

## 开源协议
  housesSys使用Apache2.0开源协议

## 功能
  ### [业务登录注册]
  
      基本登录
  ### [房屋基本资料]
  
  部门管理
  岗位信息
  员工信息

## 技术栈
  
## 创建配置
 spring.xml配置
  <!--配置数据源 -->
	<bean id="datasource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
	 	<property name="driverClassName" value="com.mysql.jdbc.Driver"/>
<!--	 	<property name="url" value="jdbc:mysql://192.168.6.150:3306/housesdb?useUnicode=true&amp;characterEncoding=UTF-8&amp;allowMultiQueries=true"/>-->
		<property name="url" value="jdbc:mysql://******/####?useUnicode=true&amp;characterEncoding=UTF-8&amp;allowMultiQueries=true"/>
		<property name="username" value="###"/>
	 	<property name="password" value=""/>
	 </bean>
	<!--配置sessionFactory -->
	 <bean id="sqlSessionFactoryBean" class="org.mybatis.spring.SqlSessionFactoryBean">
		 <property name="dataSource" ref="datasource"/>
		 <property name="configLocation" value="classpath:SqlMapConfig.xml"/>
	 </bean>
	<!--自动扫描dao接口 -->
	<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
		<!--DAO接口所在包名，spring会自动查找 -->
		<property name="basePackage" value="com.ws.dao"/>
		<property name="sqlSessionFactoryBeanName" value="sqlSessionFactoryBean"/>
	</bean>
<!--	 -->
<!--	 <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">-->
<!--	 	<property name="basePackage" value="com.ws.dao"></property>-->
<!--	 	<property name="sqlSessionFactory" ref="sqlSessionFactoryBean"></property>-->
<!--	 </bean>   -->
	<!--声明式事务管理 -->
	<bean id="transactionManager"
		  class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
		<property name="dataSource" ref="datasource"/>
	</bean>
	<!--自动扫描，标注springb注解的类自动转化为Bean -->
	 <context:component-scan base-package="com.ws"/>
	 
springmvc.xml配置
	<!--自动扫描该包 -->
	<context:component-scan base-package="com.ws.controller"/>
	<!--视图解析器 -->
	<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
		<property name="prefix" value="/"/>
		<property name="suffix" value=".jsp"/>
	</bean>
	<!--配置映射器和适应器 -->
	<mvc:annotation-driven/>
  
  
  

