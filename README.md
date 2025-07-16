# SpringBoot-WebApplication

## Tutorial Of Implementation at Below  :
## https://www.youtube.com/@devopsshack



Kubectl commands :

kubectl exec -it deploy/jenkins -- cat /var/jenkins_home/secrets/initialAdminPassword


For windows git jenkins pipeline task :-

pipeline {
    agent any
    
    tools {
        jdk 'jdk11'
        maven 'maven3'
    }

    stages {
        stage('Git Checkout ') {
            steps {
                bat 'git config --global http.sslVerify false'
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Nikhilgujela/SpringBoot-WebApplication.git'
            }
        }
        
        stage('Code Compile') {
            steps {
                    bat "mvn clean package"
            }
        }
        
        stage('Run Test Cases') {
            steps {
                    bat "mvn test"
            }
        }
    }
}
