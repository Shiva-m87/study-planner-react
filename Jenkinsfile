pipeline {
    agent any

    environment {
        IMAGE_NAME = "react-app"
        CONTAINER_NAME = "react-container"
        PORT = "3000"
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Shiva-m87/study-planner-react.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

       stage('Stop Old Container') {
    steps {
        sh '''
        docker ps -q --filter "name=react-container" | xargs -r docker stop
        docker ps -aq --filter "name=react-container" | xargs -r docker rm
        '''
    }
}

        stage('Run New Container') {
    steps {
        sh '''
        docker run -d -p 3000:80 --name react-container react-app
        '''
    }
}
    }

    post {
        success {
            echo "✅ Deployment Successful! App running on port 3000"
        }
        failure {
            echo "❌ Pipeline Failed! Check logs"
        }
    }
}
