pipeline {
    agent any
    stages {
        stage("Verify tooling") {
            steps {
                sh '''
                    docker info
                    docker version
                    docker-compose version
                '''
            }
        }
        
        stage("Start Docker") {
            steps {
                sh 'docker-compose up -d'
                sh 'docker-compose ps'
            }
        }
        stage("Run Composer Install") {
            steps {
                sh 'docker-compose run --rm composer install'
            }
        }         
        stage("Run Tests") {
            steps {
                sh 'docker-compose run --rm artisan test'
            }
        }
    }
    
}