pipeline{
    agent any
    stages{
        stage ("Build Docker Image"){
            steps{
                echo "Build Docker Image"
                bat "docker build -t mywebapp ."
            }
        }
        stage ("Docker Login"){
            steps{
                bat "docker login -u shivani1128 -p srinija63"
            }
        }
        stage("push Docker Iamge to Docker Hub"){
            steps {
                echo "push Docker Image to docker hub"
                bat "docker tag mywebapp shivani1128/sample:latest"
                bat "docker push shivani1128/sample:latest"
            }
        }
        stage("Deploy to Kubernetes"){
            steps{
                bat "kubectl apply -f deployment.yaml --validate=false"
                bat "kubectl apply -f service.yaml"
            }
        }
    }
    post{
        success{
            echo 'Pipeline completed scucessfull!'
        }
        failure{
            echo "Pipeline failed.Please check the logs."
        }
    }
}
