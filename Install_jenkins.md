https://www.jenkins.io/doc/book/installing/linux/

```
sudo apt update
sudo apt install openjdk-17-jdk -y
java -version
```
```
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]"  https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

```
sudo apt update
sudo apt install jenkins
jenkins --version
```

```
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```
You can try using curl to display your public IP. Here are a few options:
- curl ifconfig.me
- curl ipinfo.io/ip
- curl icanhazip.com

