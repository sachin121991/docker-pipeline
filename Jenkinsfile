node {
   
  stage 'Checkout'
  git 'https://github.com/sachin121991/docker-pipeline.git'
 
  stage 'Docker build'
  docker.build('sachin1291/docker-slave')
 
  stage 'Docker push'
  docker.withRegistry( 'https://registry.hub.docker.com', 'dockerhub' ) {
   docker.image.push()
   }
}
