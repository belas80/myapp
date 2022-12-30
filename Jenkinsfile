node {
  registry = "belas80/myapp"
  stage ('Cloning Git'){
    git branch: 'main', credentialsId: 'github', url: 'git@github.com:belas80/myapp.git'
  }
  stage ('Building image'){
    if (env.TAG_NAME =~ '^v') {
        myAppTag = "${env.TAG_NAME}"
    } else {
        myAppTag = "${env.BUILD_NUMBER}"
    }
    myApp = docker.build "$registry:$myAppTag"
  }
  stage ('Pushing image'){
    docker.withRegistry('', 'dockerhub') {
      myApp.push()
    }
  }
  stage ('Deploying image'){
    if (env.TAG_NAME =~ '^v') {
      sh "qbec apply stage --vm:ext-str myapp_image_tag=$myAppTag"
    }
  }
  stage ('Remove Unused docker image'){
    sh "docker rmi ${myApp.imageName()}"
  }
}