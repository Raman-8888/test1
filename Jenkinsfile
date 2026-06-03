pipeline {
    
    agent any
    environment { IMAGE = "raman8888/jenkins-demo-app" }
    
    stages {
        stage('Build') {
            steps {
                script { docker.build("${IMAGE}:${BUILD_NUMBER}") }
            }
        }
    }
}