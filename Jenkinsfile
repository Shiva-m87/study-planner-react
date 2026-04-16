pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-app-image")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker stop my-app || true'
                    sh 'docker rm my-app || true'
                    sh 'docker run -d -p 3000:3000 --name my-app my-app-image'
                }
            }
        }
    }
}
