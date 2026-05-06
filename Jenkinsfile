pipeline {
    agent any

    environment {
        IMAGE = 'sihiy1/satekontol:latest'
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE -f dockerfile .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $IMAGE'
            }
        }

        stage('Deploy Docker Swarm') {
            steps {
                sh 'docker stack deploy -c docker-stack.yml satekontol'
            }
        }
    }
}
