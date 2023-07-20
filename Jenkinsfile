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
                        echo 'Code Review'
                    }
                }
            }
        }
    }
}
