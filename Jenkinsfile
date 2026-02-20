pipeline {

    // agent any
    agent {
        docker {
            image 'docker:24-dind'  // Docker-in-Docker pour build/export
            args '--privileged -v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage("Build containers") {
            steps {
                // !!!! Attention !!!! : Assurez-vous que :
                // 1. Docker est installé et configuré sur votre machine Jenkins.
                // 2. Votre Jenkins a les permissions nécessaires pour exécuter des commandes Docker.
                sh 'docker --version'
                sh 'pwd'
                sh 'ls -la'
                sh 'ls /home'
                // On utilise "|| true" pour éviter que le pipeline échoue si le conteneur n'existe pas ou est déjà arrêté
                // sh 'docker compose -f /opt/deployment/local/docker-compose.yml stop back || true'
                // On supprime l'image existante pour éviter les conflits.
                // sh 'docker image rm -f my-node-app || true'
                // sh 'docker build -t my-node-app .'
            }
        }

        // stage('Stop existing container') {
        //     steps {
        //         // On supprime le container existant pour éviter les conflits.
        //         sh 'docker compose -f /opt/deployment/local/docker-compose.yml rm back || true'
        //     }
        // }

    //     stage('Run container') {
    //         steps {
    //             sh 'docker compose -f /opt/deployment/local/docker-compose.yml up  back -d'
    //         }
    //    }
    }
}