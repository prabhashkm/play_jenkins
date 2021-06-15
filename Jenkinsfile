pipeline {

  environment {
    dockeruser = "prabhatthedockerguy"
    dockerpass = "IamusingDocker"
  }

  agent any 
    
  stages {
    stage('build and publish') {
      steps{
        withCredentials([usernamePassword(credentialsId: 'DockerCredentialsForGitHub', passwordVariable: 'dockerpass', usernameVariable: 'dockeruser')]) {
        sh "echo \"FROM debian:latest\" > Dockerfile"
        sh "echo \"RUN apt-get update && apt-get install -y git\" >> Dockerfile"
        sh "docker login --username $dockeruser --password $dockerpass"
        sh "docker build -t prabhatthedockerguy/customdebian:${BUILD_NUMBER} --pull=true ."
        sh "docker push prabhatthedockerguy/customdebian:${BUILD_NUMBER}"
	}
      }
    }
  }

}
