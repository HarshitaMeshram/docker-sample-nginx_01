pipeline {
    agent any
    environment {
        DOCKER_HUB_CRED_DEV = credentials('Docker-Hub-Cred-Dev')
        DOCKER_HUB_CRED_QA = credentials('DOCKER-CRED-QA')
    }
    stages {
        stage('Build Docker Image for DEV') {
            when {
                branch 'dev'
            }            
            steps {
                script {
                    def dockerImage = docker.build("harshitameshram/dev:latest")
                    dockerImage.push()
                }
            }
        }
        stage('Build Docker Image for QA') {
            when {
                branch 'qa'
            }            
            steps {
                script {
                    def dockerImage = docker.build("harshitameshram/qa:latest")
                    dockerImage.push()
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
