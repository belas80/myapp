pipeline {
  environment {
    registry = "belas80/myapp"
    registryCredential = "dockerhub"
  }
  agent any
  stages {
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Pushing image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Deploy') {
      when { tag "v*" }
      steps {
        echo "Deploying only because this commit is tagged... $BRANCH_NAME:$TAG_NAME"
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}