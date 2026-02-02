pipeline {
    agent any
    
    tools {
        maven "Maven-3.9"
        jdk "JDK21"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/PriyaKitty98/hello-ci-cd-jenkins.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Archive Artifacts') {
            steps {
                echo 'Now Archieving it...'
                archiveArtifacts artifacts: '/target/*.jar', fingerprint: true  //archives the jar file
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'pipeline failed'
        }
    }
}