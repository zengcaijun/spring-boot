## 北明软件SpringBoot入门简易教程

### 入门课程之一  Eclipse

​	在学习SSM(H)的过程中，需要做大量的配置工作，其实很多配置行为本身只是手段，并不是目的。 基于这个考虑，把该简化的简化，该省略的省略，开发人员只用关心提供业务功能就行了，这就是 SpringBoot。 
换言之，SpringBoot可以简单地看成简化了的、按照约定开发的SSM(H)。 开发速度大大提升。 可是呢，最好还是有 SSM(H)的基础，否则其中用到了Spring MVC,Mybatis,Hibernate的地方，或觉得摸不着头脑。 
注： 括弧里的(H)表示Hibernate.

*步骤 1 : 关于JDK版本*    
*步骤 2 : 关于IDE*    
*步骤 3 : 关于STS插件*    
*步骤 4 : 先运行，看到效果，再学习*    
*步骤 5 : 模仿和排错*    
*步骤 6 : 关于 Tomcat*    
*步骤 7 : 创建项目*    
*步骤 8 : 输入项目参数*    
*步骤 9 : pom.xml*    
*步骤 10 : Application.java*    
*步骤 11 : HelloController.java*    
*步骤 12 : 运行并测试*   

#### **步骤 1 : 关于JDK版本**    

​	至少使用JDK8版本，请下载JDK8或者更高版本。

#### **步骤 2 : 关于IDE**

​	目前公司的开发工作是Eclipse。

#### **步骤 3 : 关于STS插件**

​	Eclipse 提供了一个专门开发 SpringBoot 的插件叫做 Spring Tool Suite. 这个插件的安装是使用国外的源，安装很卡，起码几十分钟去了。而SpringBoot 应用，本质上是一个Java 程序，其采用的风格是 maven 风格，所以又是一个 Maven 项目，接下来我们就按照 maven 项目的方式创建就行了。 不要被花里胡哨的插件掩盖了其本质。

![52950097195](D:\培训课件\images\1529500971958.png)

![52950103996](D:\培训课件\images\1529501039960.png)

![52950109721](D:\培训课件\images\1529501097217.png)

![52950134120](D:\培训课件\images\1529501341203.png)

![52950140010](C:\Users\HP\AppData\Local\Temp\1529501400106.png)

![52950144028](D:\培训课件\images\1529501440284.png)

![52950150524](D:\培训课件\images\1529501505241.png)

![52950155200](D:\培训课件\images\1529501552009.png)



#### 步骤 4 : 先运行，看到效果，再学习

​	老规矩，先导入可运行项目spring boot examples-1，配置运行起来，确认可用之后，再学习做了哪些步骤以达到这样的效果。 
这是一个 maven 项目， Eclipse 导入 maven 项目的办法，请参考如下步骤：在 Eclipse 中导入 maven 项目
然后运行类： cn.com.bmsoft.springboot.Application 的主方法
接着访问地址:http://127.0.0.1:8080/hello

![52950229746](D:\培训课件\images\1529502297465.png)

ps：在 Eclipse 中导入 maven 项目

![52950179403](D:\培训课件\images\1529501794034.png)

![52950183649](D:\培训课件\images\1529501836499.png)

![52950191871](D:\培训课件\images\1529501918710.png)

#### **步骤 5 : 模仿和排错** 

​	在确保可运行项目能够正确无误地运行之后，再严格照着教程的步骤，对代码模仿一遍。 模仿过程难免代码有出入，导致无法得到期望的运行结果，此时此刻通过比较正确答案 ( 可运行项目 ) 和自己的代码，来定位问题所在。 采用这种方式，学习有效果，排错有效率，可以较为明显地提升学习速度，跨过学习路上的各个槛。 

#### **步骤 6 : 关于 Tomcat ** 

​	先运行，看到效果，再学习 跑成功的同学，可能有一点会觉得很奇怪。 这明明跑动起来的是一个 web 程序，为什么启动方式不是启动 tomcat？ 而是启动的一个 Java 类的 主方法？ 这是因为这个 cn.com.bmsoft.springboot.Application 类的主方法就把 tomcat 嵌入进去了，不需要手动启动 tomcat 了呢。

#### 步骤 7 : 创建项目

​	接下来就开始从0开始创建这个项目了。
	首先新建个 maven 项目
	菜单 -> File -> New -> Other -> Maven -> Maven -> Maven Project -> New Maven Project
	勾上这个 Create a simple project (skip archetype selection), 看吧，Springboot就是个简单的maven 项目

​	注： 创建项目之前，要把 先运行，看到效果，再学习 步骤里启动的程序退掉先，否则会出问题。

![52950254597](D:\培训课件\images\1529502545979.png)

![52950259792](D:\培训课件\images\1529502597921.png)

![52950264735](D:\培训课件\images\1529502647356.png)

#### 步骤 8 : 输入项目参数

![52950274010](D:\培训课件\images\1529502740104.png)

#### 步骤 9 : pom.xml

​	用以下pom.xml里面的内容覆盖掉项目里的pom.xml。
	覆盖后，右键点击项目->Maven->Update Project 更新一下项目。

![52950282865](D:\培训课件\images\1529502828655.png)

![52950288841](D:\培训课件\images\1529502888413.png)



    <?xml version="1.0" encoding="UTF-8"?>
    
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    
        <modelVersion>4.0.0</modelVersion>
    
      <groupId>cn.com.bmsoft</groupId>
    
      <artifactId>springboot</artifactId>
    
      <version>1.0.0</version>
    
      <name>springboot</name>
    
      <description>springboot</description>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.14.RELEASE</version>
    </parent>
    
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
    	      <groupId>junit</groupId>
    	      <artifactId>junit</artifactId>
    	      <version>3.8.1</version>
    	      <scope>test</scope>
        </dependency>
    </dependencies>
    
    <properties>
        <java.version>1.8</java.version>
    </properties>
    
    
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
    </project>

#### 步骤 10 : Application.java  

​	创建 Application.java，其注解 @SpringBootApplication 表示这是一个SpringBoot应用，运行其主方法就会启动tomcat,默认端口是8080

	package cn.com.bmsoft.springboot;
	
	import org.springframework.boot.SpringApplication;
	import org.springframework.boot.autoconfigure.SpringBootApplication;
	
	@SpringBootApplication
	public class Application {
	
		public static void main(String[] args) {
			// TODO Auto-generated method stub
			SpringApplication.run(Application.class, args);
		}
	}

#### 步骤 11 : HelloController.java    

​	接着创建控制器类HelloController， 这个类就是Spring MVC里的一个普通的控制器。
	@RestController 是spring4里的新注解，是@ResponseBody和@Controller的缩写。

	package cn.com.bmsoft.springboot.web;
	
	import org.springframework.web.bind.annotation.RequestMapping;
	import org.springframework.web.bind.annotation.RestController;
	
	@RestController
	public class HelloController {
	
		@RequestMapping("/hello")
		public String hello() {
			return "Hello Spring Boot!";
		}
	}
#### 步骤 12 : 运行并测试 

​	接下来就运行[Application.java](http://how2j.cn/k/springboot/springboot-eclipse/1640.html#step7122)， 然后访问地址:http://127.0.0.1:8080/hello

​	就能看到测试效果了

![52950312328](D:\培训课件\images\1529503123287.png)

思考：

在控制器类HelloController中增加以下方法，并测试。

		@RequestMapping("/hello/{name}")
		public String helloWithPathVariable(@PathVariable String name) {
			return "【helloWithPathVariable】 hello " + name;
		}
		
		@RequestMapping("/hello/")
		public String helloWithRequestParam(@RequestParam String name) {
			return "【helloWithRequestParam】 hello " + name;
		}
### 入门课程之二  部署jar 方式

*步骤 1 : 部署方式*    
*步骤 2 : 可运行项目*    
*步骤 3 : 打包成jar*   
*步骤 4 : 运行该jar*    

#### 步骤 1 : 部署方式

​	Springboot 和我们之前学习的web 应用程序不一样，其本质上是一个 Java 应用程序，那么又如何部署呢？ 
	通常来说，Springboot 部署会采用两种方式：全部打包成一个jar，或者打包成一个war。
	本知识点讲解jar的方式。

#### 步骤 2 : 可运行项目

​	打开上节课程讲到的springboot项目的文件，如图所示目录

![52950322254](D:\培训课件\images\1529503222546.png)

#### 步骤 3 : 打包成jar

​	切换到 C:\eclipse-workspace\springboot目录下

```
cd C:\eclipse-workspace\springboot
mvn install	
```

![52950340467](D:\培训课件\images\1529503404674.png)

这会导致在C:\eclipse-workspace\springboot\target 目录下生成一个springboot-1.0.0.jar文件

![52950348218](C:\Users\HP\AppData\Local\Temp\1529503482182.png)

#### 步骤 4 : 运行该jar

​	接着输入命令：

​	`java -jar target/springboot-1.0.0.jar`

![52950359555](D:\培训课件\images\1529503595551.png)

### 入门课程之三  部署war 方式

*步骤 1 : 部署方式*    
*步骤 2 : 可运行项目*    
*步骤 3 : Application*   
步骤 4 : pom.xml  
*步骤 5 : 创建war包*    
*步骤 6 : 重命名 war 包，然后部署*   
*步骤 7 : 启动并测试* 

#### 步骤 1 : 部署方式

​	Springboot 和我们之前学习的web 应用程序不一样，其本质上是一个 Java 应用程序，那么又如何部署呢？
	通常来说，Springboot 部署会采用两种方式：全部打包成一个jar，或者打包成一个war。
	本知识点讲解 war 的方式。

#### 步骤 2 : 可运行项目

​	打开上节课程讲到的springboot项目的文件，如图所示目录

![52947682120](D:\培训课件\images\1529503955602.png)

#### 步骤 3 : Application

​	Application 修改为如下代码
	新加@ServletComponentScan注解，并且继承SpringBootServletInitializer 。

    package cn.com.bmsoft.springboot;
    
    import org.springframework.boot.SpringApplication;
    import org.springframework.boot.autoconfigure.SpringBootApplication;
    import org.springframework.boot.builder.SpringApplicationBuilder;
    import org.springframework.boot.web.servlet.ServletComponentScan;
    import org.springframework.boot.web.support.SpringBootServletInitializer;
    
    @SpringBootApplication
    @ServletComponentScan
    public class Application extends SpringBootServletInitializer {
    
        @Override
        protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
            return application.sources(Application.class);
        }
     	
    	public static void main(String[] args) {
    		// TODO Auto-generated method stub
    		SpringApplication.run(Application.class, args);
    	}
    
    }

#### 步骤 4 : pom.xml

​	pom.xml修改为如下代码，主要两个改动
	新加打包成war的声明：

​	`<packaging>war</packaging>`

    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
    
      <groupId>cn.com.bmsoft</groupId>
      <artifactId>springboot</artifactId>
      <version>1.0.0</version>
      <name>springboot</name>
      <description>springboot</description>
      <packaging>war</packaging>
      
        <parent>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-parent</artifactId>
            <version>1.5.14.RELEASE</version>
        </parent>
    
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-web</artifactId>
            </dependency>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-tomcat</artifactId>   
            </dependency>        
    	    <dependency>
    		      <groupId>junit</groupId>
    		      <artifactId>junit</artifactId>
    		      <version>3.8.1</version>
    		      <scope>test</scope>
    	    </dependency>
        </dependencies>
    
        <properties>
            <java.version>1.8</java.version>
        </properties>
    
    
        <build>
            <plugins>
                <plugin>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-maven-plugin</artifactId>
                </plugin>
            </plugins>
        </build>
    
    </project>

#### 步骤 5 : 创建war包

```
cd C:\eclipse-workspace\springboot -war
mvn clean package	
```

![52950417719](D:\培训课件\images\1529504177193.png)

​	这样就在 target 目录下 生成了一个 springboot-1.0.0.war 文件

![52950422941](D:\培训课件\images\1529504229412.png)

#### 步骤 6 : 重命名 war 包，然后部署 

​	如果用 springboot-1.0.0.war 这个文件名部署，那么访问的时候就要在路径上加上springboot-1.0.0。 所以把这个文件重命名为 ROOT.war，然后把它放进tomcat 的webapps目录下。

![52950438364](D:\培训课件\images\1529504383646.png)

![52950442844](D:\培训课件\images\1529504428441.png)

#### 步骤 7 : 启动并测试 

​	运行tomcat下的 bin目录里的startup.bat, 然后就可以启动了. 启动后访问如下地址测试：http://127.0.0.1:8080/hello

![52950453863](D:\培训课件\images\1529504538630.png)

![52950466531](D:\培训课件\images\1529504665314.png)

### 入门课程之四  Mybatis注解方式

*步骤 1 : 关于Mybatis*    
*步骤 2 : 创建数据库*    
*步骤 3 : 创建表*   
步骤 4 : 准备数据  
*步骤 5 : 先运行，看到效果，再学习*    
*步骤 6 : 模仿和排错*   
*步骤 7 : application.properties*    
*步骤 8 : pom.xml*   
步骤 9 : Category  
*步骤 10 : CategoryMapper*    
*步骤 11 : CategoryController*   
*步骤 12 : listCategory.jsp*   
*步骤 13: 重启测试*

#### 步骤 1 : 关于Mybatis 

​	Mybatis 是用来进行数据库操作的框架，如果没有相关知识最好学习一下。

#### 步骤 2 : 创建数据库 

​	创建数据库，名称是 studyDB。

`CREATE DATABASE IF NOT EXISTS studyDB DEFAULT CHARACTER SET = utf8mb4;`

#### 步骤 3 : 创建表 

​	创建个分类表，字段很简单，就id和name。

```
CREATE TABLE `t_category` (
  `Id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(30) DEFAULT NULL,
  PRIMARY KEY (`Id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```

#### 步骤 4 : 准备数据 

​	插入4条数据。

```
insert into t_category values(null,'category 1');
insert into t_category values(null,'category 2');
insert into t_category values(null,'category 3');
insert into t_category values(null,'category 4');
```

#### 步骤 4 : 先运行，看到效果，再学习

####  ![52950709285](D:\培训课件\images\1529507092855.png)

#### 步骤 6 : 模仿和排错 

​	在确保可运行项目能够正确无误地运行之后，再严格照着教程的步骤，对代码模仿一遍。 
	模仿过程难免代码有出入，导致无法得到期望的运行结果，此时此刻通过比较正确答案 ( 可运行项目 ) 和自己的代码，来定位问题所在。 
	采用这种方式，学习有效果，排错有效率，可以较为明显地提升学习速度，跨过学习路上的各个槛。 

#### 步骤 7 : application.properties   

​	新增数据库链接必须的参数

```
spring.mvc.view.prefix=/WEB-INF/jsp/
spring.mvc.view.suffix=.jsp
spring.datasource.url=jdbc:mysql://192.168.1.187:3306/studyDB?characterEncoding=UTF-8
spring.datasource.username=root
spring.datasource.password=newpassword
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
```

#### 步骤 8 : pom.xml 

​	增加对mysql和mybatis的支持

![52950770805](D:\培训课件\images\1529507708058.png)

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

  <groupId>cn.com.bmsoft</groupId>
  <artifactId>springboot</artifactId>
  <version>1.0.0</version>
  <name>springboot</name>
  <description>springboot</description>
  
  
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.14.RELEASE</version>
    </parent>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
            
        </dependency>
	    <dependency>
		      <groupId>junit</groupId>
		      <artifactId>junit</artifactId>
		      <version>3.8.1</version>
		      <scope>test</scope>
	    </dependency>
  		<!-- servlet依赖. -->
        <dependency>
              <groupId>javax.servlet</groupId>
              <artifactId>javax.servlet-api</artifactId>
              
        </dependency>
              <dependency>
                     <groupId>javax.servlet</groupId>
                     <artifactId>jstl</artifactId>
              </dependency>
        <!-- tomcat的支持.-->
        <dependency>
               <groupId>org.apache.tomcat.embed</groupId>
               <artifactId>tomcat-embed-jasper</artifactId>
               
        </dependency>	    
		<dependency>
		    <groupId>org.springframework.boot</groupId>
		    <artifactId>spring-boot-devtools</artifactId>
		    <optional>true</optional> <!-- 这个需要为 true 热部署才有效 -->
		</dependency>

		<!-- mybatis -->
		<dependency>
			<groupId>org.mybatis.spring.boot</groupId>
			<artifactId>mybatis-spring-boot-starter</artifactId>
			<version>1.3.2</version>
		</dependency>
		<!-- mysql -->
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<scope>runtime</scope>
		</dependency>
		
    </dependencies>
	

    <properties>
        <java.version>1.8</java.version>
    </properties>


    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>
```

#### 步骤 9 : Category

​	增加一个包：cn.com.bmsoft.springboot.pojo，然后创建实体类Category。

```
package cn.com.bmsoft.springboot.pojo;

public class Category {
 
    private int id;
     
    private String name;
    public int getId() {
        return id;
    }
    public void setId(int id) {
        this.id = id;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
     
}
```

#### 步骤 10 : CategoryMapper 

​	增加一个包：cn.com.bmsoft.springboot.mapper，然后创建接口CategoryMapper。
	使用注解@Mapper 表示这是一个Mybatis Mapper接口。
	使用@Select注解表示调用findAll方法会去执行对应的sql语句。 

```
    @Select("select id,name from t_category ")
    List<Category> findAll();

    @Select("select id,name from t_category where id=#{id}")
    List<Category> findByID(@Param("id")int id);
```

```
package cn.com.bmsoft.springboot.mapper;

import java.util.List;

import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Param;
import org.apache.ibatis.annotations.Select;

import cn.com.bmsoft.springboot.pojo.Category;

@Mapper
public interface CategoryMapper {

    @Select("select id,name from t_category ")
    List<Category> findAll();

    @Select("select id,name from t_category where id=#{id}")
    List<Category> findByID(@Param("id")int id);

}
```

#### 步骤 11 : CategoryController

​		增加一个包：cn.com.bmsoft.springboot.mapper，然后创建接口CategoryMapper。
		1. 接受listCategory映射。
		2. 然后获取所有的分类数据。
		3. 接着放如Model中。
		4. 跳转到listCategory.jsp中。

```
package cn.com.bmsoft.springboot.web;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;

import cn.com.bmsoft.springboot.mapper.CategoryMapper;
import cn.com.bmsoft.springboot.pojo.Category;
  
@Controller
public class CategoryController {
    @Autowired CategoryMapper categoryMapper;
     
    @RequestMapping("/listCategory")
    public String listCategory(Model model) throws Exception {
        List<Category> cs=categoryMapper.findAll();
         
        model.addAttribute("cs", cs);
         
        return "listCategory";
    }
    
    @RequestMapping("/listCategory/{id}")
    public String listCategoryByID(Model model,@PathVariable int id) throws Exception {
        List<Category> cs=categoryMapper.findByID(id);
         
        model.addAttribute("cs", cs);
         
        return "listCategory";
    }
     
}
```

#### 步骤 12 : listCategory.jsp 

​	用jstl遍历从CategoryController 传递过来的集合：cs. 

```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
 
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
   
<table align='center' border='1' cellspacing='0'>
    <tr>
        <td>id</td>
        <td>name</td>
    </tr>
    <c:forEach items="${cs}" var="c" varStatus="st">
        <tr>
            <td>${c.id}</td>
            <td>${c.name}</td>
                
        </tr>
    </c:forEach>
</table>
```

#### 步骤 13 : 重启测试  

​	因为在pom.xml中增加了jar包的以来，所以仅仅通过Springboot本身的热部署是无法起作用的，得手动重启一下。
	然后访问测试地址：http://127.0.0.1:8080//listCategory

![52950885496](D:\培训课件\images\1529508854967.png)

### 入门课程之五  Mybatis分页

*步骤 1 : Mybatis CRUD和分页*    
*步骤 2 : 先运行，看到效果，再学习*    
*步骤 3 : 模仿和排错  
步骤 4 : 基于前面的知识点  
*步骤 5 : pom.xml*    
*步骤 6 : PageHelperConfig  
*步骤 7 : CategoryMapper*    
*步骤 8 : CategoryController*   
步骤 9 : listCategory.jsp  
*步骤 10 : editCategory.jsp*    
*步骤 11 : 重启测试访问*   

#### 步骤 1 : Mybatis CRUD和分页

#### 	这里使用Mybatis来做一个完整的CRUD和分页。 [PageHelper官方https://github.com/pagehelper/Mybatis-PageHelper]() 

#### 步骤 2 : 先运行，看到效果，再学习

​	测试地址：http://127.0.0.1:8080/listCategory?start=2&size=3

![52953495960](D:\培训课件\images\1529534959605.png)

#### 步骤 3 : 模仿和排错

​	在确保可运行项目能够正确无误地运行之后，再严格照着教程的步骤，对代码模仿一遍。 
	模仿过程难免代码有出入，导致无法得到期望的运行结果，此时此刻通过比较正确答案 ( 可运行项目 ) 和自己的代码，来定位问题所在。 
	采用这种方式，学习有效果，排错有效率，可以较为明显地提升学习速度，跨过学习路上的各个槛。 

#### 步骤 4 : 基于前面的知识点 

​	本知识点基于上节Mybatis注解方式进行扩展学习。

#### 步骤 5 : pom.xml

​	增加对PageHelper的支持。

![52953526829](D:\培训课件\images\1529535268299.png)

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

  <groupId>cn.com.bmsoft</groupId>
  <artifactId>springboot</artifactId>
  <version>1.0.0</version>
  <name>springboot</name>
  <description>springboot</description>
  
  
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.14.RELEASE</version>
    </parent>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
            
        </dependency>
	    <dependency>
		      <groupId>junit</groupId>
		      <artifactId>junit</artifactId>
		      <version>3.8.1</version>
		      <scope>test</scope>
	    </dependency>
  		<!-- servlet依赖. -->
        <dependency>
              <groupId>javax.servlet</groupId>
              <artifactId>javax.servlet-api</artifactId>
              
        </dependency>
              <dependency>
                     <groupId>javax.servlet</groupId>
                     <artifactId>jstl</artifactId>
              </dependency>
        <!-- tomcat的支持.-->
        <dependency>
               <groupId>org.apache.tomcat.embed</groupId>
               <artifactId>tomcat-embed-jasper</artifactId>
               
        </dependency>	    
		<dependency>
		    <groupId>org.springframework.boot</groupId>
		    <artifactId>spring-boot-devtools</artifactId>
		    <optional>true</optional> <!-- 这个需要为 true 热部署才有效 -->
		</dependency>

		<!-- mybatis -->
		<dependency>
			<groupId>org.mybatis.spring.boot</groupId>
			<artifactId>mybatis-spring-boot-starter</artifactId>
			<version>1.3.2</version>
		</dependency>
		<!-- mysql -->
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<scope>runtime</scope>
		</dependency>
		<!-- pagehelper -->
		<dependency>
			<groupId>com.github.pagehelper</groupId>
			<artifactId>pagehelper</artifactId>
			<version>4.1.6</version>
		</dependency>		
    </dependencies>
	

    <properties>
        <java.version>1.8</java.version>
    </properties>


    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>
```

#### 步骤 6 : PageHelperConfig

​	注解@Configuration 表示PageHelperConfig 这个类是用来做配置的。
	注解@Bean 表示启动PageHelper这个拦截器。

​	新增加一个包 cn.com.bmsoft.springboot.config， 然后添加一个类PageHelperConfig ，其中进行PageHelper相关配置。
	offsetAsPageNum:设置为true时，会将RowBounds第一个参数offset当成pageNum页码使用。

```
p.setProperty("offsetAsPageNum", "true");
```

​	rowBoundsWithCount:设置为true时，使用RowBounds分页会进行count查询。

```
p.setProperty("rowBoundsWithCount", "true");
```

​	reasonable：启用合理化时，如果pageNum<1会查询第一页，如果pageNum>pages会查询最后一页。

```
p.setProperty("reasonable", "true");
```

```
package cn.com.bmsoft.springboot.config;

import java.util.Properties;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import com.github.pagehelper.PageHelper;

@Configuration
public class PageHelperConfig {

    @Bean
    public PageHelper pageHelper() {
        PageHelper pageHelper = new PageHelper();
        Properties p = new Properties();
        p.setProperty("offsetAsPageNum", "true");
        p.setProperty("rowBoundsWithCount", "true");
        p.setProperty("reasonable", "true");
        pageHelper.setProperties(p);
        return pageHelper;
    }
}
```

#### 步骤 7 : CategoryMapper  

​	修改CategoryMapper，增加CRUD方法的支持。 其实就是调用不同的SQL语句。

```
package cn.com.bmsoft.springboot.mapper;

import java.util.List;

import org.apache.ibatis.annotations.Delete;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;
import org.apache.ibatis.annotations.Update;

import cn.com.bmsoft.springboot.pojo.Category;

@Mapper
public interface CategoryMapper {

    @Select("select * from t_category ")
    List<Category> findAll();
    
    @Insert(" insert into t_category ( name ) values (#{name}) ") 
    public int save(Category category);  
    
    @Delete(" delete from t_category where id= #{id} ") 
    public void delete(int id); 
        
    @Select("select * from t_category where id= #{id} ") 
    public Category get(int id); 
      
    @Update("update t_category set name=#{name} where id=#{id} ") 
    public int update(Category category);  

}
```

#### 步骤 8 : CategoryController 

​	为CategoryController添加： 增加、删除、获取、修改映射。

```
    @RequestMapping("/addCategory")
    public String listCategory(Category c) throws Exception {
    	categoryMapper.save(c);
    	return "redirect:listCategory";
    }
    @RequestMapping("/deleteCategory")
    public String deleteCategory(Category c) throws Exception {
    	categoryMapper.delete(c.getId());
    	return "redirect:listCategory";
    }
    @RequestMapping("/updateCategory")
    public String updateCategory(Category c) throws Exception {
    	categoryMapper.update(c);
    	return "redirect:listCategory";
    }
    @RequestMapping("/editCategory")
    public String listCategory(int id,Model m) throws Exception {
    	Category c= categoryMapper.get(id);
    	m.addAttribute("c", c);
    	return "editCategory";
    }
```

​	修改查询映射。

    	@RequestMapping("/listCategory")
    	public String listCategory(Model m,@RequestParam(value = "start", defaultValue = "0") int start,@RequestParam(value = "size", defaultValue = "5") int size) throws Exception {
    	    PageHelper.startPage(start,size,"id desc");
    	    List<Category> cs=categoryMapper.findAll();
    	    PageInfo<Category> page = new PageInfo<>(cs);
    	    m.addAttribute("page", page);         
    	    return "listCategory";
    	}
        
​	1.在参数里接受当前是第几页 start ，以及每页显示多少条数据 size。 默认值分别是0和5。

	@RequestParam(value = "start", defaultValue = "0") int start,@RequestParam(value = "size", defaultValue = "5"

​	2.根据start,size进行分页，并且设置id 倒排序。

```
PageHelper.startPage(start,size,"id desc");
```

​	3.因为PageHelper的作用，这里就会返回当前分页的集合了。

```
List<Category> cs=categoryMapper.findAll();
```

​	4.根据返回的集合，创建PageInfo对象。

```
PageInfo<Category> page = new PageInfo<>(cs);
```

​	5.把PageInfo对象扔进model，以供后续显示。

```
m.addAttribute("page", page);   
```

​	6.跳转到listCategory.jsp。

```
return "listCategory";
```

```
package cn.com.bmsoft.springboot.web;
import java.util.List;
  
@Controller
public class CategoryController {
    @Autowired CategoryMapper categoryMapper;
     
    
    @RequestMapping("/addCategory")
    public String listCategory(Category c) throws Exception {
    	categoryMapper.save(c);
    	return "redirect:listCategory";
    }
    @RequestMapping("/deleteCategory")
    public String deleteCategory(Category c) throws Exception {
    	categoryMapper.delete(c.getId());
    	return "redirect:listCategory";
    }
    @RequestMapping("/updateCategory")
    public String updateCategory(Category c) throws Exception {
    	categoryMapper.update(c);
    	return "redirect:listCategory";
    }
    @RequestMapping("/editCategory")
    public String listCategory(int id,Model m) throws Exception {
    	Category c= categoryMapper.get(id);
    	m.addAttribute("c", c);
    	return "editCategory";
    }
    
	@RequestMapping("/listCategory")
	public String listCategory(Model m,@RequestParam(value = "start", defaultValue = "0") int start,@RequestParam(value = "size", defaultValue = "5") int size) throws Exception {
	    PageHelper.startPage(start,size,"id desc");
	    List<Category> cs=categoryMapper.findAll();
	    PageInfo<Category> page = new PageInfo<>(cs);
	    m.addAttribute("page", page);         
	    return "listCategory";
	}
       
}
```

#### 步骤 9 : listCategory.jsp

​	通过page.getList遍历当前页面的Category对象。
	在分页的时候通过page.pageNum获取当前页面，page.pages获取总页面数。
	注：page.getList会返回一个泛型是Category的集合。

```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
 
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
   
<div align="center">
 
</div>
 
<div style="width:500px;margin:20px auto;text-align: center">
    <table align='center' border='1' cellspacing='0'>
        <tr>
            <td>id</td>
            <td>name</td>
            <td>编辑</td>
            <td>删除</td>
        </tr>
        <c:forEach items="${page.list}" var="c" varStatus="st">
            <tr>
                <td>${c.id}</td>
                <td>${c.name}</td>
                <td><a href="editCategory?id=${c.id}">编辑</a></td>
                <td><a href="deleteCategory?id=${c.id}">删除</a></td>
            </tr>
        </c:forEach>
         
    </table>
    <br>
    <div>
                <a href="?start=1&size=${page.pageSize}">[首  页]</a>
            <a href="?start=${page.pageNum-1}&size=${page.pageSize}">[上一页]</a>
            <a href="?start=${page.pageNum+1}&size=${page.pageSize}">[下一页]</a>
            <a href="?start=${page.pages}&size=${page.pageSize}">[末  页]</a>
    </div>
    <br>
    <form action="addCategory" method="post">
     
    name: <input name="name"> <br>
    <button type="submit">提交</button>
     
    </form>
</div>


```

#### 步骤 10 : editCategory.jsp

​	修改分类的页面

```
<%@ page language="java" contentType="text/html; charset=UTF-8"
 pageEncoding="UTF-8" isELIgnored="false"%>
 
<div style="margin:0px auto; width:500px">
 
<form action="updateCategory" method="post">
 
name: <input name="name" value="${c.name}"> <br>
 
<input name="id" type="hidden" value="${c.id}">
<button type="submit">提交</button>
 
</form>
</div>
```

#### 步骤 11 : 重启测试访问 

​	访问测试地址：http://127.0.0.1:8080/listCategory?start=2&size=3

![52953707709](D:\培训课件\images\1529537077098.png)