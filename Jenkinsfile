pipeline {
    agent {
        docker {
            image 'docker:dind'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    
    stages {
        stage('Hello World') {
            steps {
                sh 'echo "Hello World"'
            }
        }
    }
}

