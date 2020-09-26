pipeline {
   agent any

   stages {
      stage('Jenkinsfile-Test') {
         steps {
            script{
                //git branch: 'Your Branch name', credentialsId: 'Your crendiatails', url: ' Your BitBucket Repo URL '
                git branch: 'master', credentialsId: 'bitbucket-cred', url: 'https://bitbucket.org/jenkins-all-in-one/just-test/'
                //To read file from workspace which will contain the Jenkins Job Name ###
                def filePath = readFile "${env.WORKSPACE}/versions.txt"                   
                //To read file line by line ###
                def lines = filePath.readLines() 
                 
                //To iterate and run Jenkins Jobs one by one ####
                for (line in lines) { 
                     try {                                           
                    echo "$line"
                    } catch (Exception e) {
                     echo "Loop failed, but we continue"
                }  
            }
             
        }
      }
   }
   stage('Jenkins-workspace') {
   steps {
       script {
           sh "ls -la ${pwd()}"  
           sh "tree ${env.WORKSPACE}"
       }
    }
   }
 }
}