pipeline {
  environment {
    registry = "belas80/myapp"
    registryCredential = "dockerhub"
  }
  agent any
  stages {
    stage('Building image') {
      steps {
        echo "Current TAG_NAME = ${env.TAG_NAME}"
        script {
          if ("$TAG_NAME" == "v*") {
              echo "Deploying only because this commit is tagged... $registry:$TAG_NAME"
          } else {
              echo "Current TAG_NAME = $registry:${env.BUILD_NUMBER}"
          }
        }
      }
    }
  }
}