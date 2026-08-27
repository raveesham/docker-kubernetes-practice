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
                echo "Building my-website:${env.BUILD_NUMBER}..."
                bat "docker build -t my-website:${env.BUILD_NUMBER} task1-html"
            }
        }

        stage('Run Container Test') {
            steps {
                echo 'Starting test container...'
                bat "docker run -d --name jenkins-my-website-test -p 8084:80 my-website:${env.BUILD_NUMBER}"
            }
        }

        stage('Test Website') {
            steps {
                echo 'Testing Nginx inside the container...'
                bat  '''
            powershell -NoProfile -Command "$response = Invoke-WebRequest -UseBasicParsing http://localhost:8084; if ($response.StatusCode -ne 200) { exit 1 }; Write-Host 'Website test successful - HTTP 200'"
        '''
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