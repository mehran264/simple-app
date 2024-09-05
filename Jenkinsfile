pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git 'https://github.com/your-github-username/simple-app.git'
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
