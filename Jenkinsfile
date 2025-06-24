pipeline {
    agent any
    environment {
        IMAGE = "djilalidernane/devops"
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/DJDERNANE/devops-lab.git'
            }
        }
         stage('test') {
            steps {
                echo "donne"
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker push $IMAGE'
                }
            }
        }
    }
}
