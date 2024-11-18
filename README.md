# parquet_installation

1) Go to https://openstack.cern.ch/project/instances/.
2) Launch an ALMA9 x86_64 m2.small machine.
3) ssh as root to the machine from lxplus (e.g. `ssh root@amlevin1`)
4) `yum -y install wget`
5) `yum -y install emacs`
6) `yum install -y java-1.8.0-openjdk-devel.x86_64`
7) `yum -y groupinstall "Development Tools"`
8) `wget -nv https://archive.apache.org/dist/thrift/0.21.0/thrift-0.21.0.tar.gz`
9) `tar xzf thrift-0.21.0.tar.gz`
10) `cd thrift-0.21.0`
11) `chmod +x ./configure`
12) `./configure --disable-libs`
13) `make install -j 1`
14) `cd ../`
15) `git clone https://github.com/apache/parquet-java.git`
16) `cd parquet-java/`
17) remove the line `"<module>parquet-scala</module>"` from the file pom.xml
18) `LC_ALL=C ./mvnw clean install -DskipTests=true`
19) `./mvnw dependency:copy-dependencies`
20) `cd parquet-cli`
21) `java -cp 'target/parquet-cli-1.15.0-SNAPSHOT.jar:target/dependency/*' org.apache.parquet.cli.Main`
