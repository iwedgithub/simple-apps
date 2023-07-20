pipeline {
   agent {
        node {
            label 'devops-iwed'
        }
    }

    stages {
        stage('Build Apps') {
            steps {
               sh 'npm install'
            }
        }
        stage('Run Test') {
            parallel {
                 stage('Unit Test') {
                    steps {
                        sh '''npm test
                        npm run test:coverage'''
                    }
                }
                stage('Code Review') {
                    steps {
                        sh 'sonar-scanner   -Dsonar.projectKey=project-iwed   -Dsonar.sources=.   -Dsonar.host.url=http://10.23.2.3:9000   -Dsonar.login=sqp_878a619a613ddbbfe9ffa7eebd9ca8c6818331a2'
                    }
                }
            }
        }
        stage('Build Image') {
            steps {
               sh 'docker compose build'
            }
        }
        stage('Push Image') {
            steps {
               sh 'docker compose push'
            }
        }
        stage('Deploy Apps') {
            steps {
               sh 'docker compose up -d'
            }
        }
    }
}
