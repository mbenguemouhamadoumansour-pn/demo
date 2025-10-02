pipeline {
    agent any

    environment {
        DOCKER_COMPOSE_FILE = 'docker-compose.yml'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/mbenguemouhamadoumansour-pn/demo.git', branch: 'master'
            }
        }

        stage('Build Docker Images') {
            steps {
                script {
                    sh "docker-compose -f $DOCKER_COMPOSE_FILE build --no-cache"
                }
            }
        }

        stage('Deploy Containers') {
            steps {
                script {
                    sh "docker-compose -f $DOCKER_COMPOSE_FILE up -d"
                }
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline terminé avec succès !"
        }
        failure {
            echo "❌ Il y a eu une erreur dans le pipeline."
        }
    }
}
