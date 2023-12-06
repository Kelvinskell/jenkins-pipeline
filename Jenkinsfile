pipeline {
    agent any
    
    stages{
        stage('SonarQube analysis') {
      steps {
        script {
          // requires SonarQube Scanner 2.8+
          scannerHome = tool 'SonarScanner'
        }
        withSonarQubeEnv('SonarQube Server') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }

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
        stage('Push image to Dockerhub') {
            steps {
                script{
                    withCredentials([string(credentialsId: 'DockerHubPass', variable: 'DockerHubpass')]) {
                    sh 'docker login -u kelvinskell --password ${DockerHubpass}' }
                    sh 'docker push kelvinskell/python-http-server'
                }
            }
        }    
}
        post {
        always {
            // Always executed
                sh 'docker rm python-app'
        }
        success {
            // on sucessful execution
            sh 'docker logout'   
        }
    }
}