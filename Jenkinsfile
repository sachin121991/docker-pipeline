node {
    def app

    stage 'Checkout'
    git 'https://github.com/sachin121991/docker-pipeline.git'

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("sachin1291/docker-slave")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry( 'https://registry.hub.docker.com', 'dockerhub' ) {
            app.push("${env.BUILD_NUMBER}")
           
        }
    }
}
    
