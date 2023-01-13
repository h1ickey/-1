# 1.简介

![image-20220926234435663](typora图片/image-20220926234435663.png)

![image-20220926234501992](typora图片/image-20220926234501992.png)

# 2.Spring入门案例

![image-20220926234533615](typora图片/image-20220926234533615.png)

![image-20220926234701669](typora图片/image-20220926234701669.png)

![image-20220926234801106](typora图片/image-20220926234801106.png)

![image-20220926234825148](typora图片/image-20220926234825148.png)

![image-20220927000942460](typora图片/image-20220927000942460.png)

![image-20220927001204021](typora图片/image-20220927001204021.png)

![image-20220927001220171](typora图片/image-20220927001220171.png)

![image-20220927001239210](typora图片/image-20220927001239210.png)

![image-20220927001252541](typora图片/image-20220927001252541.png)

![image-20220927001305441](typora图片/image-20220927001305441.png)

![image-20220927001335424](typora图片/image-20220927001335424.png)

![image-20220927001405829](typora图片/image-20220927001405829.png)

![image-20220927001536893](typora图片/image-20220927001536893.png)

## 1.Controller加载控制与业务bean加载控制

![image-20220927001723876](typora图片/image-20220927001723876.png)

![image-20220927002139134](typora图片/image-20220927002139134.png)

# 3.Postman

![image-20220927002322308](typora图片/image-20220927002322308.png)









# 4.请求与响应

![image-20220927100004292](typora图片/image-20220927100004292.png)

![image-20220927162047240](typora图片/image-20220927162047240.png)

```java
import org.springframework.web.context.WebApplicationContext;
import org.springframework.web.context.support.AnnotationConfigWebApplicationContext;
import org.springframework.web.filter.CharacterEncodingFilter;
import org.springframework.web.servlet.support.AbstractDispatcherServletInitializer;

import javax.servlet.Filter;

//定义一个servlet容器启动的配置类，在里面加载spring的配置
public class InitConfig extends AbstractDispatcherServletInitializer {
    //加载springMVC容器配置
    @Override
    protected WebApplicationContext createServletApplicationContext() {
        AnnotationConfigWebApplicationContext ctx = new AnnotationConfigWebApplicationContext();
        ctx.register(SpringMvcConfig.class);
        return ctx;
    }

    //设置那些请求归属springMVC处理
    @Override
    protected String[] getServletMappings() {
        return new String[]{"/"};
    }

    //加载spring容器配置
    @Override
    protected WebApplicationContext createRootApplicationContext() {
        return null;
    }

    //乱码处理
    @Override
    protected Filter[] getServletFilters() {
        CharacterEncodingFilter fileter = new CharacterEncodingFilter();
        fileter.setEncoding("UTF-8");
        return new Filter[]{fileter};
    }
}
```

## 4.1POST请求中文乱码的问题

![image-20220927162812207](typora图片/image-20220927162812207.png)

## 4.2.不同类型传参

![image-20220927164111018](typora图片/image-20220927164111018.png)

![image-20220927164130939](typora图片/image-20220927164130939.png)

![image-20220927164159456](typora图片/image-20220927164159456.png)

![image-20220927164218311](typora图片/image-20220927164218311.png)

![image-20220927164233424](typora图片/image-20220927164233424.png)

## 4.3传递json数据类型

导入json坐标

```xml
 <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-databind</artifactId>
            <version>2.9.0</version>
        </dependency>
```

![image-20220927171750467](typora图片/image-20220927171750467.png)

![image-20220927193021875](typora图片/image-20220927193021875.png)

![image-20220927193049259](typora图片/image-20220927193049259.png)



![image-20220927193118461](typora图片/image-20220927193118461.png)

![image-20220927193135693](typora图片/image-20220927193135693.png)

![image-20220927193149147](typora图片/image-20220927193149147.png)

![image-20220927193210224](typora图片/image-20220927193210224.png)



## 4.4日期类型转换

![image-20220927194157161](typora图片/image-20220927194157161.png)

![image-20220927194216465](typora图片/image-20220927194216465.png)

![image-20220927194254771](typora图片/image-20220927194254771.png)

## 4.5响应

![image-20220927195824380](typora图片/image-20220927195824380.png)

<img src="typora图片/image-20220927195835596.png" alt="image-20220927195835596" style="zoom:50%;" />

<img src="typora图片/image-20220927195858225.png" alt="image-20220927195858225" style="zoom:50%;" />

<img src="typora图片/image-20220927195924773.png" alt="image-20220927195924773" style="zoom:50%;" />



<img src="typora图片/image-20220927200018328.png" alt="image-20220927200018328" style="zoom:67%;" />

![image-20220927200152088](typora图片/image-20220927200152088.png)



# 5.REST风格

## 5.1简介

![image-20220927200426718](typora图片/image-20220927200426718.png)

![image-20220927201238561](typora图片/image-20220927201238561.png)

## 5.2入门案例

![image-20220927210919935](typora图片/image-20220927210919935.png)

![image-20220927210942495](typora图片/image-20220927210942495.png)

![image-20220927211018569](typora图片/image-20220927211018569.png)

![image-20220927211033238](typora图片/image-20220927211033238.png)

![image-20220927211051263](typora图片/image-20220927211051263.png)

## 5.3RESTful快速开发

![image-20220927212413455](typora图片/image-20220927212413455.png)

![image-20220927212427597](typora图片/image-20220927212427597.png)

## 5.4设置对静态资源的访问放行

```java
@Configuration
public class SpringMvcSupport extends WebMvcConfigurationSupport {
    @Override
    protected void addResourceHandlers(ResourceHandlerRegistry registry) {
        //当访问/page/？？？时候不要走mvc/走page目录下的内容
        registry.addResourceHandler("/pages/**").addResourceLocations("/pages/");
        registry.addResourceHandler("/css/**").addResourceLocations("/css/");
        registry.addResourceHandler("/js/**").addResourceLocations("/js/");
        registry.addResourceHandler("/plugins/**").addResourceLocations("/plugins/");
    }
}
```

![image-20220929003040436](typora图片/image-20220929003040436.png)









# 6.SSM整合

## 1.导入的坐标

```xml
   <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>5.2.10.RELEASE</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>5.2.10.RELEASE</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-test</artifactId>
            <version>5.2.10.RELEASE</version>
        </dependency>

        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.5.6</version>
        </dependency>

        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis-spring</artifactId>
            <version>1.3.0</version>
        </dependency>

        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.47</version>
        </dependency>

        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid</artifactId>
            <version>1.1.16</version>
        </dependency>

        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>

        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>3.1.0</version>
            <scope>provided</scope>
        </dependency>

        <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-databind</artifactId>
            <version>2.9.0</version>
        </dependency>
    </dependencies>
    <build>
        <resources>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
        </resources>
    </build>
```

![image-20220929143306125](typora图片/image-20220929143306125.png)

## 2.spring

**SpringConfig**

```java
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Import;
import org.springframework.context.annotation.PropertySource;
import org.springframework.transaction.annotation.EnableTransactionManagement;

@Configuration
@ComponentScan({"com.service"})
@PropertySource("classpath:jdbc.properties")
@Import({JdbcConfig.class,MyBatisConfig.class})
@EnableTransactionManagement
public class SpringConfig {
}
```

## 3.mybatis

**MybatisConfig**

```java
import org.mybatis.spring.SqlSessionFactoryBean;
import org.mybatis.spring.mapper.MapperScannerConfigurer;
import org.springframework.context.annotation.Bean;

import javax.sql.DataSource;

public class MyBatisConfig {

    @Bean
    public SqlSessionFactoryBean sqlSessionFactory(DataSource dataSource){
        SqlSessionFactoryBean factoryBean = new SqlSessionFactoryBean();
        factoryBean.setDataSource(dataSource);

        return factoryBean;
    }

    @Bean
    public MapperScannerConfigurer mapperScannerConfigurer(){
        MapperScannerConfigurer msc = new MapperScannerConfigurer();
        msc.setBasePackage("com.dao");
        return msc;
    }

}
```

**JDBCConfig**

```java
import com.alibaba.druid.pool.DruidDataSource;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.jdbc.datasource.DataSourceTransactionManager;
import org.springframework.transaction.PlatformTransactionManager;

import javax.sql.DataSource;

public class JdbcConfig {
    @Value("${jdbc.driver}")
    private String driver;
    @Value("${jdbc.url}")
    private String url;
    @Value("${jdbc.username}")
    private String username;
    @Value("${jdbc.password}")
    private String password;

    @Bean
    public DataSource dataSource(){
        DruidDataSource dataSource = new DruidDataSource();
        dataSource.setDriverClassName(driver);
        dataSource.setUrl(url);
        dataSource.setUsername(username);
        dataSource.setPassword(password);
        return dataSource;
    }

    @Bean
    public PlatformTransactionManager transactionManager(DataSource dataSource){
        DataSourceTransactionManager ds = new DataSourceTransactionManager();
        ds.setDataSource(dataSource);
        return ds;
    }
}

```

**jdbc.properties**

```properties
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/ssm_db
jdbc.username=root
jdbc.paassword=root
```

## 4.springmvc

**SpringMvcConfig**

```java
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.EnableWebMvc;

@Configuration
@ComponentScan({"com.controller","com.config"})
@EnableWebMvc
public class SpringMvcConfig {
}
```



**ServletConfig**

```java
import org.springframework.web.servlet.support.AbstractAnnotationConfigDispatcherServletInitializer;

public class ServletConfig extends AbstractAnnotationConfigDispatcherServletInitializer {
    protected Class<?>[] getRootConfigClasses() {
        return new Class[]{SpringConfig.class};
    }

    protected Class<?>[] getServletConfigClasses() {
        return new Class[]{SpringMvcConfig.class};
    }

    protected String[] getServletMappings() {
        return new String[]{"/"};
    }
}
```

SpringMvcSupport

```java
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.ResourceHandlerRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurationSupport;

@Configuration
public class SpringMvcSupport extends WebMvcConfigurationSupport {
    @Override
    protected void addResourceHandlers(ResourceHandlerRegistry registry) {
        //当访问/page/？？？时候不要走mvc/走page目录下的内容
        registry.addResourceHandler("/pages/**").addResourceLocations("/pages/");
        registry.addResourceHandler("/css/**").addResourceLocations("/css/");
        registry.addResourceHandler("/js/**").addResourceLocations("/js/");
        registry.addResourceHandler("/plugins/**").addResourceLocations("/plugins/");
    }
}
```



![image-20220930143358902](typora图片/image-20220930143358902.png)

## 5.表现层数据封装

![image-20220930164322658](typora图片/image-20220930164322658.png)

![image-20220930172033882](typora图片/image-20220930172033882.png)

![image-20220930172053993](typora图片/image-20220930172053993.png)

## 6.异常处理器

![image-20220930172359376](typora图片/image-20220930172359376.png)

![image-20220930172455932](typora图片/image-20220930172455932.png)

![image-20220930203244039](typora图片/image-20220930203244039.png)

![image-20220930203305692](typora图片/image-20220930203305692.png)

![image-20220930203911858](typora图片/image-20220930203911858.png)

![image-20220930203930307](typora图片/image-20220930203930307.png)

![image-20220930204404614](typora图片/image-20220930204404614.png)

![image-20220930205835762](typora图片/image-20220930205835762.png)

### 1.自定义系统异常

![image-20220930205948669](typora图片/image-20220930205948669.png)

### 2.自定义业务异常

![image-20220930210021878](typora图片/image-20220930210021878.png)

### 3.自定义异常编码(持续补充)

![image-20220930210106820](typora图片/image-20220930210106820.png)

### 4.触发自定义异常

![image-20220930210140729](typora图片/image-20220930210140729.png)

### 5.拦截并处理异常

![image-20220930210226633](typora图片/image-20220930210226633.png)

### 6.异常处理器效果对比

![image-20220930210409865](typora图片/image-20220930210409865.png)

# 7.拦截器

![image-20221001124859790](typora图片/image-20221001124859790.png)

![image-20221002144927261](typora图片/image-20221002144927261.png)

![image-20221002145000788](typora图片/image-20221002145000788.png)

![image-20221002160537853](typora图片/image-20221002160537853.png)

![image-20221002160556073](typora图片/image-20221002160556073.png)

![image-20221002160626810](typora图片/image-20221002160626810.png)

![image-20221002160835889](typora图片/image-20221002160835889.png)

## 1.执行流程

![image-20221002161000389](typora图片/image-20221002161000389.png)

![image-20221002161018846](typora图片/image-20221002161018846.png)

## 2.拦截器的参数

![image-20221002161331528](typora图片/image-20221002161331528.png)

![image-20221002161405322](typora图片/image-20221002161405322.png)

![image-20221002161419796](typora图片/image-20221002161419796.png)

## 3.多拦截器的执行顺序

![image-20221002161814230](typora图片/image-20221002161814230.png)

# 8.分模块开发

## 1.分模块开发意义

![image-20221002162046998](typora图片/image-20221002162046998.png)

## 2.分模块开发

![image-20221002162826446](typora图片/image-20221002162826446.png)

![image-20221002162948352](typora图片/image-20221002162948352.png)

![image-20221002163000214](typora图片/image-20221002163000214.png)
