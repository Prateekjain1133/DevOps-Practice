pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/Prateekjain1133/DevOps-Practice.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Stop Old App') {
            steps {
                sh 'pm2 stop demo-node || true'
                sh 'pm2 delete demo-node || true'
            }
        }

        stage('Start App') {
            steps {
                sh 'pm2 start index.js --name devops-practice'
            }
        }
    }
}
