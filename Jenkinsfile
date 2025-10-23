pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Build Docker Image"
                bat 'docker build -t hello-world-flask .'
            }
        }
        stage('Run') {
            steps {
                echo "Run Docker Container"
                bat 'docker rm -f hello-container || exit 0'
                bat 'docker run -d -p 5000:5000 --name hello-container hello-world-flask'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs.'
        }
    }
}
