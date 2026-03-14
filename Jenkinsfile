pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Shubham-Kumar1/shopflow-k8s.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'sonar-scanner'
                    withSonarQubeEnv('sonarqube-server') {
                        sh """
                        ${scannerHome}/bin/sonar-scanner \
                        -Dsonar.projectKey=shopflow-k8s \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://34.180.25.168:9000
                        """
                    }
                }
            }
        }

    }
}
