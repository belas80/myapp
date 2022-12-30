pipeline {
  environment {
    registry = "belas80/myapp"
    registryCredential = "dockerhub"
  }
  agent any
  stages {
    stage('Building image') {
      steps {
        echo "Current TAG_NAME = $TAG_NAME"
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy') {
      when { tag "v*" }
      steps {
        echo "Deploying only because this commit is tagged... $registry:$TAG_NAME"
      }
    }
  }
}