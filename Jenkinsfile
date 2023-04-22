pipeline{
    agent{
        docker {
            image 'urmilkalaria/cc_project:latest'
        }
    }
    stages{
        stage('Build Docker Image'){
            steps{
                sh 'sudo docker build . -t django-ecommerce'
            }
        }
        stage('Push Docker Image to DockerHub') {
            steps{
                sh 'sudo docker login -u urmilkalaria -p patel17042002'
                sh 'sudo docker tag django-ecommerce urmilkalaria/cc_project'
                sh 'sudo docker push urmilkalaria/cc_project'
            }
        }
        stage('Test Application') {
            steps{
                sh 'sudo docker pull urmilkalaria/cc_project'
                sh 'sudo docker run -d -p 8000:8000 urmilkalaria/cc_project'
                sh 'sudo docker ps'
            }
        }
    }
    post {
        always {
            sh 'echo "Pipeline Finished."'
        }
    }
}