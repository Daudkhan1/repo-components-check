pipeline {
    agent {
        kubernetes {
            yamlFile 'pod.yaml'
        }
    }
    
    environment {
        registry = 'daudidrees/my-image'
        registryCredential = 'dockerhub'
    }
    
    stages {
        stage('Docker build image') {
            steps {
                container('docker') {
                    sh 'docker build -t daudidrees/my-image .'
                }
            }
        }
        
        stage('scan image') {
            steps {
                container('trivy') {
                    sh 'trivy image daudidrees/my-image'
                }
            }
        }
        
        stage('docker push image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1', registryCredential) {
                        docker.image('daudidrees/my-image').push()
                    }
                }
            }
        }
    }
}
