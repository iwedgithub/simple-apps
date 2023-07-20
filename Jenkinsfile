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
            paralel {
                 stage('Unit Test') {
                    steps {
                        echo 'Unit Test'
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
