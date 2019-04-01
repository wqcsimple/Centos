# Maven Gradle 安装

## 安装java
```shell
yum -y list java*
yum install -y java-1.8.0-openjdk-devel.x86_64
```

## 安装Gradle
```shell
wget https://downloads.gradle.org/distributions/gradle-5.1.1-all.zip

mkdir /opt/gradle
unzip -d /opt/gradle gradle-5.1.1-all.zip

vim /etc/profile

PATH=$PATH:/opt/gradle/gradle-5.1.1/bin
export PATH

source /etc/profile

vi gradle.properties
org.gradle.daemon=true
org.gradle.parallel=true
org.gradle.jvmargs=-Xms100m -Xmx200m
```


## 安装Maven
```shell
wget http://apache.fayea.com/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz

mkdir /opt/maven
mv apache-maven-3.6.0-bin.tar.gz /opt/maven

cd /opt/maven & tar -zxvf apache-maven-3.6.0-bin.tar.gz

vim /etc/profile

export MAVEN_HOME=/opt/maven/apache-maven-3.6.0
export PATH=${MAVEN_HOME}/bin:${PATH}

source /etc/profile

查看是否安装成功
mvn -v
```


## Maven项目切换Gradle项目
```shell
再Maven根目录下运行
gradle init --type pom
运行成功之后运行命令gradle build，成功之后删除pom.xml即可。
```