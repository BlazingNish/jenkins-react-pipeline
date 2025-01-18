pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Linting') {
            steps {
                sh 'npm run lint'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build Project') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'rm -rf /var/www/react-app/*'
                sh 'cp -r build/* /var/www/react-app/'
            }
        }

        stage('Post-Deployment Test') {
            steps {
                sh 'curl -I http://localhost'
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
