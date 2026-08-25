pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Project') {
            steps {
                echo 'Checking docker-kubernetes-practice project...'
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Verify Docker') {
            steps {
                sh 'docker --version'
            }
        }
    }

    post {
        success {
            echo 'CI pipeline completed successfully.'
        }

        failure {
            echo 'Pipeline failed. Check Console Output.'
        }
    }
}