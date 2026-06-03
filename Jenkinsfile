pipeline {
    
    agent any
    environment { IMAGE = "raman8888/jenkins-demo-app" }
    
    stages {
        stage('Build') {
            steps {
                script { docker.build("${IMAGE}:${BUILD_NUMBER}") }
            }
        }
        
        stage('Push') {
            options {
                timeout(time: 15, unit: 'MINUTES')
            }
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                        docker.image("${IMAGE}:${BUILD_NUMBER}").push()
                        docker.image("${IMAGE}:latest").push()
                    }
                }
            }
        }
    }
}