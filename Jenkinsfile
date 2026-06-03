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
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub_creds') {
                        docker.image("${IMAGE}:${BUILD_NUMBER}").push()
                        docker.image("${IMAGE}:${BUILD_NUMBER}").push('latest')
                    }
                }
            }
        }
    }
}