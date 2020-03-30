node {
  stage 'Checkout'
  git 'https://github.com/sachin121991/docker-pipeline-demo.git'
 
  stage 'Docker build'
  docker.build('testing')
 
  stage 'Docker push'
  docker.withRegistry('https://617375091432.dkr.ecr.us-west-2.amazonaws.com/testing', 'ecr:us-west-2:aws') {
    docker.image('testing').push('latest')
  }
}
