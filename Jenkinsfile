pipeline {
    environment {
    registry = "dlfarande/devops_pipeline_jenkins"
    registryCredential = 'dockerhubcredentials'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Checkout') 
    {
      steps {
        git credentialsId: 'githubcredentials', url: 'https://github.com/dlfarande/Jenkinsfile_raj_training.git'
      }
    }
    stage('Docker Build') {
      steps{
        script {
          dockerImage = docker.build registry + ":latests-$BUILD_NUMBER"
        }
      }
    }
    stage('Docker Push') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
           dockerImage.push()
          }
        }
      }
    }
  }
}
