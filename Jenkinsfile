pipeline {
    agents any 
    stages {
        stage('Build Docker Image') {
            steps {
                echo 'Build Docker Image'
                bat 'docker build -t mywebapp .'
            }
        }
        stage('Docker login') {
            steps {
                bat 'docker login -u shivani1128 -p srinija63'
            }
        }
        stage('Push Docker Image to Docker Hub') {
            steps {
                echo 'Push Docker Image to Docker Hub'
                bat 'docker tag mywebapp shivani1128/sample:latest'
                bat 'docker push shivani1128/sample:latest'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }
    post {
        success {
            echo 'Pipeline finished successfully!'
        }
        failure {
            echo 'Pipeline failed, Please check the logs'
        }
    }
}