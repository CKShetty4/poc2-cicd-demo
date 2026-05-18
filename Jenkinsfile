pipeline {
    agent any

    environment {
        IMAGE_NAME = "poc2-demo"
        CONTAINER_NAME = "poc2-container"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/CKShetty4/poc2-cicd-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f $CONTAINER_NAME || true
                docker run -d -p 8082:80 --name $CONTAINER_NAME $IMAGE_NAME
                '''
            }
        }
    }
}
