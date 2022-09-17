## Part 1 - Install Java, Maven and Git packages

- Connect to the Jenkins Server 
  
- Install Java
  
```bash
sudo yum update -y
sudo amazon-linux-extras install java-openjdk11 -y
sudo yum install java-devel 
```

- Install Maven
  
```bash
sudo su
cd /opt
rm -rf maven
wget https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz
tar -zxvf $(ls | grep apache-maven-*-bin.tar.gz)
rm -rf $(ls | grep apache-maven-*-bin.tar.gz)
sudo ln -s $(ls | grep apache-maven*) maven
echo 'export M2_HOME=/opt/maven' > /etc/profile.d/maven.sh
echo 'export PATH=${M2_HOME}/bin:${PATH}' >> /etc/profile.d/maven.sh
exit
source /etc/profile.d/maven.sh
```
- Install Git
  
```bash
sudo yum install git -y
```
## Part 2 - To change the  Language in Jenkins

- Click Jenkins’i Yönet > Eklentileri Yönet > Kullanılabilir and write locale on search bar then click Locale Plugin and click install without restart.

- Click Jenkins’i Yönet > Sistem Konfigurasyonunu and find Locale and write English and click Ignore browser preference and force this language to all users then save.

## Part 3 - Maven Settings

- Open Jenkins GUI on web browser

- Setting System Maven Path for default usage
  
- Go to `Manage Jenkins`
  - Select `Configure System`
  - Find `Environment variables` part,
  - Click `Add`
    - for `Name`, enter `PATH+EXTRA` 
    - for `Value`, enter `/opt/maven/bin`
- Save

- Setting a specific Maven Release in Jenkins for usage
  
- Go to the `Global Tool Configuration`
- To the bottom, `Maven` section
  - Give a name such as `maven-3.8.6`
  - Select `install automatically`
  - `Install from Apache` version `3.8.6`
- Save
