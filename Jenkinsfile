pipeline {
   agent any

   stages {
      stage('Jenkinsfile-readFile') {
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
   stage('Jenkins-writefile') {
   steps {
       script {
            // Make the output directory.
            sh "mkdir -p output"
            // Write an useful file, which is needed to be archived.
            writeFile file: "output/usefulfile.txt", text: "This file is useful, need to archive it."

            // Write an useless file, which is not needed to be archived.
            writeFile file: "output/uselessfile.md", text: "This file is useless, no need to archive it."
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