pipeline {
    agent any
    stages {
        stage('Build Docker Image for DEV') {
            when {
                branch 'dev'
            }            
            steps {
                script {
                    def app = docker.build("harshitameshram/dev:latest")
                    docker.withRegistry('https://registry.hub.docker.com', 'Docker-Hub-Cred-Dev') {
                        app.push()
                    }
                }
            }
        }
        stage('Build Docker Image for QA') {
            when {
                branch 'qa'
            }            
            steps {
                script {
                    def app = docker.build("harshitameshram/qa:latest")
                    docker.withRegistry('https://registry.hub.docker.com', 'DOCKER-CRED-QA') {
                        app.push()
                    }
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
