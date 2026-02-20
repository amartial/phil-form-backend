pipeline {

    agent any
    environment {
        DB_HOST = '127.0.0.1'
        DB_USER = 'db_user'
        DB_PASSWORD = 'db_password'
        DB_NAME = 'db_name'
    }

    stages {

        stage("Check Docker") {
            steps {
                sh 'whoami'
                sh 'hostname'
                sh 'docker --version'
            }
        }

        stage("Build container") {
            steps {
                sh 'docker rmi -f my-node-app || true'
                sh 'docker build -t my-node-app .'
            }
        }

        stage('Stop existing container') {
            steps {
                sh 'docker stop my-node-app || true'
                sh 'docker rm my-node-app || true'
            }
        }

        stage('Run container') {
            steps {
                sh '''
                    docker run -d --name my-node-app \
                    -p 3000:3000 \
                    -e DB_HOST=${DB_HOST} \
                    -e DB_USER=${DB_USER} \
                    -e DB_PASSWORD=${DB_PASSWORD} \
                    -e DB_NAME=${DB_NAME} \
                    my-node-app
                '''
            }
        }
    }
}