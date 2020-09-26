pipeline {
  environment {
    registry = "ajaykumar011/jenkins-node1"  //create a repo on hub.docker.com first
    registryCredential = 'dockerhub'   // create a dockerhub id credentials for login to dockerhub
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/ajaykumar011/node-todo-frontend.git'
        //copy the https git repo .git extension is required.
      }
    }
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
          docker.withRegistry( '', registryCredential ) {
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
}

// 