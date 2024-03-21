pipeline {
    agent {
        kubernetes {
            yamlFile 'pod.yaml'
        }
    }
    
    stages {
        stage('Docker build image') {
            steps {
                container('docker') {
                    sh 'docker build -t my-image .'
                }
            }
        }
        stage('scan image') {
            steps {
                container('trivy') {
                    sh 'trivy image my-image'
                }
            }
        }
    }
}
