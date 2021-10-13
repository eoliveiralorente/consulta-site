pipeline {
environment {
    registry = "eoliveiralorente/consulta-site"
    registryCredential = 'dockerhub_id'
    dockerImage = ''
}
    agent any
    
        stages {
            
        stage('Clonar git') {
          steps {
            script {
              git 'https://github.com/eoliveiralorente/consulta-site.git'
            }           
          }
        }

        stage('Docker build') {
            steps {
                script {
                 dockerImage = docker.build registry + ":$BUILD_NUMBER"   
              }
            }
        }
        
        stage('Docker push') {
            steps {
                script {
                docker.withRegistry('https://registry.hub.docker.com',registryCredential ) {
                dockerImage.push("")
                }
            }
        }
        
       }
    }
}
