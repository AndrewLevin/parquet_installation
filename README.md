# parquet_installation

1) yum -y install wget
2) yum -y install emacs
3) yum install -y java-1.8.0-openjdk-devel.x86_64
4) yum -y groupinstall "Development Tools"
5) wget -nv https://archive.apache.org/dist/thrift/0.21.0/thrift-0.21.0.tar.gz
6) tar xzf thrift-0.21.0.tar.gz
7) cd thrift-0.21.0
8) chmod +x ./configure
9) ./configure --disable-libs
10) make install -j 1
11) cd ../
12) git clone https://github.com/apache/parquet-java.git
13) cd parquet-java/
14) remove the line "<module>parquet-scala</module>" from the file pom.xml
15) LC_ALL=C ./mvnw clean install -DskipTests=true
16) ./mvnw dependency:copy-dependencies
17) cd parquet-cli
18) java -cp 'target/parquet-cli-1.15.0-SNAPSHOT.jar:target/dependency/*' org.apache.parquet.cli.Main
