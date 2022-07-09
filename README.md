# How to intercept network with Selenium Java on LambdaTest cloud.
![Java](https://www.lambdatest.com/support/assets/images/og-images/Java-with-Selenium-1-1.jpg)

### Prerequisites
1. Install and set environment variable for java.
    * Windows - https://www.oracle.com/java/technologies/downloads/
    * Linux - ```  sudo apt-get install openjdk-8-jre  ```
    * MacOS - Java should already be present on Mac OS X by default.
2 Install and set environment varibale for Maven.
    * Windows - https://maven.apache.org/install.html
    * Linux/ MacOS -  [Homebrew](http://brew.sh/) (Easier)
    ```
     install maven
    ```
### Intercept network requests

The following code can be used to intercept network requests:
```java
DevTools devTools = ((HasDevTools) driver).getDevTools();
devTools.createSession();

Supplier<InputStream> message = () -> new ByteArrayInputStream(
   "Creamy, delicious cheese!".getBytes(StandardCharsets.UTF_8));

NetworkInterceptor interceptor = new NetworkInterceptor(
   driver,
   Route.matching(req -> true)
   .to(() -> req -> new HttpResponse()
   .setStatus(200)
   .addHeader("Content-Type", StandardCharsets.UTF_8.toString())
   .setContent(message)));
```                               
### Run your First Test
1. Clone the Java-Selenium-Sample repository. 
```
git clone https://github.com/LambdaTest/java-selenium-sample.git
```
2. Next get into Java-Selenium-Sample folder, and import Lamabdatest Credentials. You can get these from lambdatest automation dashboard.
   <p align="center">
   <b>For Linux/macOS:</b>:
 
```
export LT_USERNAME="YOUR_USERNAME"
export LT_ACCESS_KEY="YOUR ACCESS KEY"
```
<p align="center">
   <b>For Windows:</b>

```
set LT_USERNAME="YOUR_USERNAME"
set LT_ACCESS_KEY="YOUR ACCESS KEY"
```
Step 3. You may also want to run the command below to check for outdated dependencies. Please be sure to verify and review updates before editing your pom.xml file as they may not be compatible with your code.
```
 mvn versions:display-dependency-updates
```
Step 4. Run single test.
```
mvn clean install exec:java -Dexec.mainClass="com.lambdatest.InterceptNetwork" -Dexec.classpathScope=test -e
```

## About LambdaTest

[LambdaTest](https://www.lambdatest.com/) is a cloud based selenium grid infrastructure that can help you run automated cross browser compatibility tests on 2000+ different browser and operating system environments. LambdaTest supports all programming languages and frameworks that are supported with Selenium, and have easy integrations with all popular CI/CD platforms. It's a perfect solution to bring your [selenium automation testing](https://www.lambdatest.com/selenium-automation) to cloud based infrastructure that not only helps you increase your test coverage over multiple desktop and mobile browsers, but also allows you to cut down your test execution time by running tests on parallel.

