pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git url: 'https://github.com/mehran264/simple-app.git', credentialsId: '05b717f6-8173-4f6f-8666-592f89f637af'
            }
        }
        
        stage('Build') {
            steps {
                script {
                    // Using Node.js Docker image to run the build
                    docker.image('node:14').inside {
                        sh 'npm install'
                    }
                }
            }
        }
        
        stage('Run Application') {
            steps {
                script {
                    // Running the app using a Docker container
                    docker.image('node:14').inside {
                        sh 'nohup npm start &'
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed!'
        }
    }
}
