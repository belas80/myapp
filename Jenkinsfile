node {
  def registry = "belas80/myapp"
  stage ('Pushing image'){
    echo "Current TAG_NAME = ${env.TAG_NAME}"
    if (env.TAG_NAME =~ '^v') {
        echo "I only execute on the master branch. Tag = $registry:${env.TAG_NAME}"
    } else {
        echo "I execute elsewhere Tag = $registry:${env.BUILD_NUMBER}"
    }
  }
}