pipeline {
    agent any
    
    stages{
        stage('Build Docker Image') {
            steps {
                script{
                    sh 'docker build -t kelvinskell/python-http-server .'
            }
        }
    }
        stage('Test image') {
            steps {
                script{
                    sh 'docker run -d --name python-app kelvinskell/python-http-server && sleep 10 && docker stop python-app'
                    sh 'docker rm python-app'
                }
            }
        }
        stage('Push image to Dockerhub') {
            steps {
                script{
                    withCredentials([string(credentialsId: 'DockerHubPass', variable: 'DockerHubpass')]) {
                    sh 'docker login -u kelvinskell -p ${DockeHubPass}' 
}
                    sh 'docker push kelvinskell/python-http-server'
                }
            }
        }    
}
}