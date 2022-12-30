node {
  registry = "belas80/myapp"
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
      echo "Deploying only because this commit is tagged... $registry:$myAppTag"
    }
  }
  stage ('Remove Unused docker image'){
    echo "bla bla bla ${myApp.imageName()}"
    sh "docker rmi $registry:$myAppTag"
  }
}