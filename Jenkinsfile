node {
  environment {
    registry = "sachin1291/docker-slave"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  stage 'Checkout'
  git 'https://github.com/sachin121991/docker-pipeline-demo.git'
 
  stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }  
  stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( 'https://registry.hub.docker.com', 'dockerhub' ) {
            dockerImage.push()
          }
        }
      }  
    }
  stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
 
}
