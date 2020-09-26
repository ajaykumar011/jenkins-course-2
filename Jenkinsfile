pipeline {
    agent any
    tools {
        maven 'maven-3.0.5'
         
    }
    stages {
        stage('Example') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}


//	The tool name must be pre-configured in Jenkins under Manage Jenkins → Global Tool Configuration.
