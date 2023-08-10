# Create EC2 with Ubuntu

![Alt text](Screenshots/3.Ansible.png)

```yml
sudo apt update
sudo apt install ansible
```
![Alt text](Screenshots/1.Ansible-Version.jpg)

![Alt text](Screenshots/3.Ansible.png)
- Installing JDK which is an important Java based package required for Jenkins to run.


```yml
sudo apt install default-jdk-headless
```

```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt-get install jenkins

sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

- Since Jenkins runs on default port 8080, open this port on the Security Group inbound rule of the jenkins server on AWS



- Login to Jenkins server: <jenkins_server_public_ip_address>:8080

## Attaching WebHook to Jenkins Server
On the github repository that contains application code, create a webhook to connect to the jenkins job. To create webhook, go to the settings tab on the github repo and click on webhooks. Webhook should look like this:

<public_ip_of_jenkins_server>:8080/github-webhook/

![Alt text](Screenshots/4.Webhook.jpg)

## Creating Job and Configuring GIT Based Push Trigger

- On the jenkins server, create a new freestyle job
In configuration of the Jenkins freestyle job choose Git repository, provide there the link to the GitHub repository and credentials (user/password) so Jenkins could access files in the repository. Also specify the branch containing code

![Alt text](<Screenshots/5.Retrive Password.jpg>)

![Alt text](<Screenshots/6.Jenkins Install.jpg>)

![Alt text](<Screenshots/7.Jenkis Ready.jpg>)

![Alt text](<Screenshots/8.Build Triggers.jpg>)

![Alt text](<Screenshots/9. Status.jpg>)
