pipeline {
    agent any
    tools {
        docker 'Docker'
    }
    
    stages{
        stage('Build Docker Image') {
            steps {
                docker build -t kelvinskell/python-http-server .
            }
        }
    }
}