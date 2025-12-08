pipeline {
    agent any

    environment {
        DOCKERHUB_USERNAME = 'risi2004'
        
        IMAGE_NAME = 'devops-capstone'

        DOCKER_CREDS_ID = 'docker-hub-repo'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    echo '--- Building Docker Image ---'
                    sh 'docker build -t $DOCKERHUB_USERNAME/$IMAGE_NAME:latest .'
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                script {
                    echo '--- Logging in to Docker Hub ---'
                    withCredentials([usernamePassword(credentialsId: DOCKER_CREDS_ID, passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {
                        sh "echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin"
                    }
                }
            }
        }

        stage('Push Image') {
            steps {
                script {
                    echo '--- Pushing Image to Docker Hub ---'
                    sh 'docker push $DOCKERHUB_USERNAME/$IMAGE_NAME:latest'
                }
            }
        }

        stage('Deploy to Server') {
            steps {
                script {
                    echo '--- Deploying Container ---'
                    // Stop and remove the old container if it exists (ignore errors if it doesn't)
                    sh 'docker stop node-app || true'
                    sh 'docker rm node-app || true'
                    
                    // Run the new container on Port 3000
                    sh 'docker run -d -p 3000:3000 --name node-app $DOCKERHUB_USERNAME/$IMAGE_NAME:latest'
                }
            }
        }
    }
}