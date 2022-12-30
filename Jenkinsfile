node {
  def registry = "belas80/myapp"
  stage ('Pushing image'){
    echo "Current TAG_NAME = ${env.TAG_NAME}"
    if (env.TAG_NAME == 'v*') {
        echo 'I only execute on the master branch. Tag = $TAG_NAME'
    } else {
        echo "I execute elsewhere Tag = ${env.BUILD_NUMBER}"
    }
  }
}