pipeline {
  environment {
    //registry = "ajaykumar011/jenkins-node1"  //create a repo on hub.docker.com first
   // registryCredential = 'dockerhub'   // create a dockerhub id credentials for login to dockerhub
    dockerImage = ''
  }
  agent any
    stages {
        stage('Build image') {
                /* This builds the actual image; synonymous to
                 * docker build on the command line */
                script {
                app = docker.build("ajaykumar011/jenkins-node2")
                }
            }
        
            stage('Test image') {
                /* Ideally, we would run a test framework against our image.
                 * For this example, we're using a Volkswagen-type approach ;-) */
                script {
                app.inside {
                    sh 'echo "Tests passed"'
                }
                }
            }
        
            stage('Push image') {
                /* Finally, we'll push the image with two tags:
                 * First, the incremental build number from Jenkins
                 * Second, the 'latest' tag.
                 * Pushing multiple tags is cheap, as all the layers are reused. */
                    script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                    }
                }
            }
        }
}