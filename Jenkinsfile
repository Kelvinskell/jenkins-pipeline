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
                }
            }
        }    
}
}