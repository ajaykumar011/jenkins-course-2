pipeline {
   agent any

   stages {
      stage('Jenkinsfile-Test') {
         steps {
            script{
                //git branch: 'Your Branch name', credentialsId: 'Your crendiatails', url: ' Your BitBucket Repo URL '
                git branch: 'master', credentialsId: 'bitbucket-cred', url: 'https://bitbucket.org/jenkins-all-in-one/just-test/'
                //To read file from workspace which will contain the Jenkins Job Name ###
                def filePath = readFile "${WORKSPACE}/versions.txt"                   
                //To read file line by line ###
                def lines = filePath.readLines() 
      
                //To iterate and run Jenkins Jobs one by one ####

                for (line in lines) {                                            
                    build(job: "$line/$branchName",
                    parameters:
                    [string(name: 'vertical', value: "${params.vert}"),
                    string(name: 'environment', value: "${params.env}"),
                    string(name: 'branch', value: "${params.branch}"),
                    string(name: 'project', value: "${params.project}")
                     ]
                    )
                   }  
         }
                
        }
      }
   }
}