pipeline {
    agent any
    
    stages {
        stage('SCM') {
            steps {
                git branch: 'webhook', url: 'https://github.com/PriyaKitty98/hello-ci-cd-jenkins.git'
            }
        }
        stage('Build and Unit Test') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Done') {
            steps {
                echo 'Pipeline steps completed now'
            }
        }
    }
}
