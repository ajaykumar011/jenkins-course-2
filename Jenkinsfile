// Using git without checkout 
pipeline {
  agent any
  parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('Example') {
      steps {
        git branch: "${params.BRANCH}", url: 'https://github.com/jenkinsci/git-parameter-plugin.git'
      }
    }
  }
}


// // Using git within checkout - This is working.
// pipeline {
//     agent any
//     parameters {
//         gitParameter name: 'TAG', 
//                      type: 'PT_TAG',
//                      defaultValue: 'master'
//     }
//     stages {
//         stage('Example') {
//             steps {
//                 checkout([$class: 'GitSCM', 
//                           branches: [[name: "${params.TAG}"]], 
//                           doGenerateSubmoduleConfigurations: false, 
//                           extensions: [], 
//                           gitTool: 'Default', 
//                           submoduleCfg: [], 
//                           userRemoteConfigs: [[url: 'https://github.com/jenkinsci/git-parameter-plugin.git']]
//                         ])
//             }
//         }
//     }
// }
