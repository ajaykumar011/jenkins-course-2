pipeline {
    agent any
    tools {
        maven 'maven-3.0.5'  //global configuration
        docker 'mydocker'
    }
    stages {
        stage('Example') {
            tools {
                maven 'maven-3.6.3'  //local configuration overriding the global
            }
            steps {
                sh 'mvn --version'  // outlput - maven 3.6.3
                sh 'docker --version'
            }
        }
    }
}


//	The tool name must be pre-configured in Jenkins under Manage Jenkins → Global Tool Configuration.
