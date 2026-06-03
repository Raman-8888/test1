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
                    bat '''
                        docker tag "%IMAGE%:%BUILD_NUMBER%" "%IMAGE%:latest"
                        docker push "%IMAGE%:%BUILD_NUMBER%"
                        docker push "%IMAGE%:latest"
                    '''
                }
            }
        }
    }
}