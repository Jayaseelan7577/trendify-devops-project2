pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'jayaseelan7577/trendify-app'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out Trendify source code'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${DOCKER_IMAGE}:latest .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASSWORD'
                )]) {
                    sh '''
                        echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USER" --password-stdin
                        docker push ${DOCKER_IMAGE}:latest
                        docker logout
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Trendify CI pipeline completed successfully!'
        }
        failure {
            echo 'Trendify CI pipeline failed.'
        }
    }
}
