pipeline {
    agent {
        kubernetes {
            yamlFile 'pod.yaml'
        }
    }
    
    stages {
        stage('Get a Maven project') {
            steps {
                container('docker') {
                    sh 'trivy image jenkins/jenkins'
                }
            }
        }
    }
}
