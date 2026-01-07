pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nginx-jenkins-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop nginx-web || true
                docker rm nginx-web || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d \
                --name nginx-web \
                -p 80:80 \
                nginx-jenkins-app
                '''
            }
        }
    }
}

