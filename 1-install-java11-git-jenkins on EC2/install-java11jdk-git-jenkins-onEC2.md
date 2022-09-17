## Part 1 - Installing Jenkins Server on Amazon Linux 2 with `yum` Repo

- Launch an AWS EC2 instance of Amazon Linux 2 AMI with security group allowing SSH and TCP 8080 ports.

- Connect to the instance with SSH.

```bash
ssh -i .ssh/call-training.pem ec2-user@ec2-3-133-106-98.us-east-2.compute.amazonaws.com
```

- Update the installed packages and package cache on your instance.

```bash
sudo yum update -y
```

- Install `Java 11 openjdk` Java Development Kit.

```bash
sudo amazon-linux-extras install java-openjdk11 -y
```

- Check the java version.

```bash
java -version
```

- Install Git

```bash
sudo yum install git -y
```

- Add Jenkins repo to the `yum` repository.

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
```

- Import a key file from Jenkins-CI to enable installation from the package.

```bash
sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
```

- Enable the EPEL repository for Amazon EC2 instance.

```bash
sudo amazon-linux-extras install epel -y
```

- Install Jenkins.

```bash
sudo yum install jenkins -y
```

- Start Jenkins service.

```bash
sudo systemctl start jenkins
```

- Enable Jenkins service so that Jenkins service can restart automatically after reboots.

```bash
sudo systemctl enable jenkins
```

- Check if the Jenkins service is up and running.

```bash
sudo systemctl status jenkins
```

- Get the initial administrative password.

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
- Open your browser, get your ec2 instance Public IPv4 DNS and paste it at address bar with 8080. 
"http://[ec2-public-dns-name]:8080"

- Enter the temporary password to unlock the Jenkins.

- Install suggested plugins.

- Create first admin user (call-jenkins:Call-jenkins1234).

- Check the URL, then save and finish the installation.

## Part 2 - To change the  Language in Jenkins

- Click Jenkins’i Yönet > Eklentileri Yönet > Kullanılabilir and write locale on search bar then click Locale Plugin and click install without restart.

- Click Jenkins’i Yönet > Sistem Konfigurasyonunu and find Locale and write English and click Ignore browser preference and force this language to all users then save.

## Part 3 - Install Plugins

- Click Manage jenkins > Plugin Manager > Avaliable and write on the search bar
    - deploy to container
    - copy artifact plugins select and click on install without restart