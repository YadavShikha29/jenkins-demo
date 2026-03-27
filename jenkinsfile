pipeline {
    agent any

    environment {
        IMAGE_NAME = "myapp"
        CONTAINER_NAME = "myapp-container"
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Run tests here"'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop $CONTAINER_NAME || true
                docker rm $CONTAINER_NAME || true
                docker run -d -p 3000:3000 --name $CONTAINER_NAME $IMAGE_NAME
                '''
            }
        }
    }
}
