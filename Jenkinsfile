pipeline {
    agent any
    stages {
        stage('Build Docker Image for DEV') {
            steps {
                script {
                    def app = docker.build("harshitameshram/dev:latest")
                    docker.withRegistry('https://registry.hub.docker.com', 'Docker-Hub-Cred-Dev') {
                        app.push('harshitameshram/dev:latest')
                    }
                }
            }
        }
        stage('Build Docker Image for QA') {
            steps {
                script {
                    def app = docker.build("harshitameshram/qa:latest")
                    docker.withRegistry('https://registry.hub.docker.com', 'DOCKER-CRED-QA') {
                        app.push('harshitameshram/qa:latest')
                    }
                }
            }
        }
    post {
        always {
            echo 'Cleaning up...'
            deleteDir()
        }
    }
    }
}
