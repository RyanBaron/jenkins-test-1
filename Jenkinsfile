
node('docker-base') {

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
