pipeline {
    agent any

    environment {
        IMAGE_NAME     = "project-frontend-image"
        CONTAINER_NAME = "project-frontend-container"
        APP_PORT       = "80"
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $IMAGE_NAME .
                '''
            }
        }

        stage('Stop Existing Container') {
            steps {
                sh '''
                if [ "$(docker ps -aq -f name=$CONTAINER_NAME)" ]; then
                    docker stop $CONTAINER_NAME || true
                    docker rm $CONTAINER_NAME || true
                fi
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d \
                --name $CONTAINER_NAME \
                -p $APP_PORT:80 \
                $IMAGE_NAME
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Frontend deployed successfully"
        }
        failure {
            echo "❌ Deployment failed"
        }
    }
}

