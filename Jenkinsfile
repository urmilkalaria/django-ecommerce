pipeline{
    agent{
        docker {
            image 'urmilkalaria/cc_project:latest'
        }
    }
    stages{
        stage('Initialize'){
            dockerHome = tool 'Docker'
            env.PATH = "${dockerHome}/bin:${env.PATH}"
        }
        stage('Build Docker Image'){
            steps{
                sh 'docker build . -t django-ecommerce'
            }
        }
        stage('Push Docker Image to DockerHub') {
            steps{
                sh 'docker login -u urmilkalaria -p patel17042002'
                sh 'docker tag django-ecommerce urmilkalaria/cc_project'
                sh 'docker push urmilkalaria/cc_project'
            }
        }
        stage('Test Application') {
            steps{
                sh 'docker pull urmilkalaria/cc_project'
                sh 'docker run -d -p 8000:8000 urmilkalaria/cc_project'
                sh 'docker ps'
            }
        }
    }
}