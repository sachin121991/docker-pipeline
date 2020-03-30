node {
   environment {
    registry = "sachin1291/docker-slave"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  stage 'Checkout'
  git 'https://github.com/sachin121991/docker-pipeline.git'
 
  stage 'Docker build'
  docker.build('testing')
 
  stage 'Docker push'
  docker.withRegistry( '', registryCredential ) {
   dockerImage.push()
   }
  }
}
