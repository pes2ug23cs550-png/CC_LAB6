pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t backend-image ./backend'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --name backend-container backend-image'
            }
        }

        stage('Run NGINX') {
            steps {
                sh 'docker run -d -p 80:80 --name nginx -v $(pwd)/nginx/default.conf:/etc/nginx/conf.d/default.conf nginx'
            }
        }
    }
}
