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
                    echo "$line"
                                   
                   }  
         }
                
        }
      }
   }
}

// env.WORKSPACE = pwd()
// def version = readFile "${env.WORKSPACE}/version.txt"
// //loop in one stage
// def stepsWithTry(list){
//     for (int i = 0; i < list.size(); i++) {
//         try {
//         sh "curl --connect-timeout 15 -v -L ${list[i]}"
//         } catch (Exception e) {
//             echo "Stage failed, but we continue"
//         }
//     }
// }