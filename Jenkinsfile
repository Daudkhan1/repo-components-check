pipeline {
    agent {
        kubernetes {
            yamlFile 'pod.yaml'
        }
    }
    
    stages {
        stage('Docker build image') {
            steps {
                container ('docker') {
                    sh 'docker build my-image .'
                }
            }
        }
        stage('Get a Maven project') {
            steps {
                container('docker') {
                    sh 'trivy image jenkins/jenkins'
                }
            }
        }
    }
}
