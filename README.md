## CI/CD set up for a java application 

- This project demostrates how to set up Nexus repository using VMs or an EC2 instance for a Java application project

### Pre-requisite Ensuer services are running on both VMs. Nexus service on port 8081 and Sonatqube service on port 9000

- Set up your VMs or provision an EC instance on AWS 
- I developed ansible playbooks for setting up Nexus server and Sonarqube servers on the VMs. 
- Use the ansible playbook to provision the required services on the VMs or EC instance 

```bash 
ssh-keygen   # Press Enter to accept default
ssh-copy-id ansibleUser@ipAddress                        | Used to copy your key to remote device or server for ansible user pumej
```
- Access the Nexus repository service on your server's ip address 

```bash
http://ipaddress:8081
```

## Create the corresonding repositories needed for our project - Vprofile java project

    - Created the below repositories 
        - vpro-maven-central        | This is where our project would download or access all dependencies for the project. This has been linked to maven repo URL - https://repo1.maven.org/maven2/. 
        - vpro maven-group          | This repository is the group for all our other repos 
        - vprofile-release          | This is where all successfully built artifacts for our project would reside 
        - vprofile-snapshot         | This is where all snapshots for our project would be saved 

## Now we can create a sample build job in jenkins 

- Update the properties section of the goal with the variables in setting.xml file 

    SNAP-REPO
    NEXUS-USER
    NEXUS-PASS
    RELEASE-REPO
    CENTRAL-REPO
    NEXUS-GRP-REPO
    NEXUSIP
    NEXUSPORT 

## Integrating Slack to jenkins for notification purposes 

    - Create a slack account and create a channel in your workspace 
    - Go to api.slack.com/apps and create an jenkins bot app and attach your workspace - Pumejlab for my case 
    - Go to oauth and permissions section and scroll down to Scopes and select chat:write
    - Then scroll back up and click install app to worksace and copy the token generated 
    - Go back to your jenkins console and install the slack plugin and also assign the credentials.
    - Also update the jenkins system configuration to use the custom bot server, add your workspace, and channel name. Test connection, you should get a success message. 
    - Now you can use the post notification features on your Build jobs. 