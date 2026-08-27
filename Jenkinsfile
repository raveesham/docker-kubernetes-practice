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
                echo 'Verifying docker-kubernetes-practice project...'
                bat 'cd'
                bat 'dir'
            }
        }

        stage('Verify Docker') {
            steps {
                echo 'Checking Docker...'
                bat 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building my-website:v1...'
                bat 'docker build -t my-website:v1 task1-html'
            }
        }

        stage('Run Container Test') {
            steps {
                echo 'Starting test container...'
                bat 'docker run -d --name jenkins-my-website-test my-website:v1'
            }
        }

        stage('Test Website') {
            steps {
                echo 'Testing Nginx inside the container...'
                bat 'docker exec jenkins-my-website-test wget -qO- http://localhost'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up test container...'
            bat 'docker rm -f jenkins-my-website-test >NUL 2>&1 || exit /b 0'
        }

        success {
            echo 'Docker CI pipeline completed successfully.'
        }

        failure {
            echo 'Pipeline failed. Check Console Output.'
        }
    }
}