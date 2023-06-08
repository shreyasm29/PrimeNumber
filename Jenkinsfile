pipeline {
  environment {
    registry = "shreyasm29/ise3"
    registryCredential = 'dockerid'
    dockerImage = ''
  }
  agent any
  
  stages {
    stage('Build Image') {
      steps {
        script {
          dockerImage = docker.build("${registry}:${BUILD_NUMBER}")
        }
      }
    }
    stage('Deploy the image') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', registryCredential) {
            dockerImage.push()
          }
        }
}
}
}
}
