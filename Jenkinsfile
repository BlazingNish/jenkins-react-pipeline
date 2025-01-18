pipeline {
    agent any

    environment {
        NODE_HOME = tool 'NodeJS'
        PATH = "${NODE_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/BlazingNish/jenkins-react-pipeline.git'
            }
        }

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
