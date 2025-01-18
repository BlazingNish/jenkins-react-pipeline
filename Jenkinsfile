pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Linting') {
            steps {
                bat 'npm run lint'
            }
        }

        stage('Build Project') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy Application') {
            steps {
                bat 'rm -rf /var/www/react-app/*'
                bat 'cp -r build/* /var/www/react-app/'
            }
        }

        stage('Post-Deployment Test') {
            steps {
                bat 'curl -I http://localhost'
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful! 🎉'
        }
        failure {
            echo 'Deployment Failed ❌'
        }
    }
}
