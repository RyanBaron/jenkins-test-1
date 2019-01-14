
//node('docker-base') { // the node here is the node that jenkins will build to.
node('jenkins_node_1') {

  echo "\nInside the docker-base\n"
  
  //////
  // properties([buildDiscarder(logRotator(numToKeepStr: '5'))])
  //////
  try {
    echo "\nInside the docker-base->try\n"
    docker.image('quay.io/pantheon-public/php-ci:latest').inside("-u root") {
    
      echo "\nInside the docker-base->try->image\n"
      properties(
        [parameters([choice(choices: "test\nprod", description: '', name: 'ENVIRONMENT'),
      ])])
    }
  }
  catch (err) {
    echo "\nInside the docker-base->catch\n"
    currentBuild.result = 'FAILED'
    throw err
  }
}
