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
    }
}
