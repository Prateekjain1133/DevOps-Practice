// pipeline {
//     agent any

//     stages {

//         stage('Clone Code') {
//             steps {
//                 git 'https://github.com/Prateekjain1133/DevOps-Practice.git'
//             }
//         }

//         stage('Install Dependencies') {
//             steps {
//                 sh 'npm install'
//             }
//         }

//         stage('Stop Old App') {
//             steps {
//                 sh 'pm2 stop demo-node || true'
//                 sh 'pm2 delete demo-node || true'
//             }
//         }

//         stage('Start App') {
//             steps {
//                 sh 'pm2 start index.js --name devops-practice'
//             }
//         }
//     }
// }

// pipeline {
//     agent any

//     stages {

//         stage('Install Dependencies') {
//             steps {
//                 sh 'npm install'
//             }
//         }

//         stage('Stop Old App') {
//             steps {
//                 sh 'pm2 stop devops-practice || true'
//                 sh 'pm2 delete devops-practice || true'
//             }
//         }

//         stage('Start App') {
//             steps {
//                 sh 'pm2 start index.js --name devops-practice'
//             }
//         }
//     }
// }


pipeline {
    agent any

    environment {
        APP_NAME = "devops-practice"
        WORKDIR = "/var/lib/jenkins/workspace/DemoPipeline"
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh '''
                  cd $WORKDIR
                  npm install
                '''
            }
        }

        stage('Stop Old App') {
            steps {
                sh '''
                  sudo -u ubuntu pm2 delete $APP_NAME || true
                '''
            }
        }

        stage('Start App') {
            steps {
                sh '''
                  sudo -u ubuntu bash << EOF
                  cd $WORKDIR
                  pm2 start index.js --name $APP_NAME
                  pm2 save
                  EOF
                '''
            }
        }
    }
}
