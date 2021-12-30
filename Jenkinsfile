// Simple script with one step: apply changes from source control linked to the app repo

// pipeline {
//     agent any

//     stages {
//         stage('preparation') {
//             steps {
//                 snApplyChanges url: "https://dev99253.service-now.com", credentialsId: "2934736d-facb-4169-a459-01f7119eddee", appScope: "x_666176_github_ci"
//             }
//         }
//     }
// }

pipeline {
  agent any
  environment {
    APPSYSID = '0f94aa8a8760011088f3ca280cbb357b'
    APPSCOPE = 'x_666176_github_ci'
    BRANCH = "${BRANCH_NAME}"
    CREDENTIALS = '2934736d-facb-4169-a459-01f7119eddee'
    DEVENV = 'https://dev117906.service-now.com/'
    TESTENV = 'https://dev99253.service-now.com/'
    TESTSUITEID = '488a2dd487031010f4cc7157f6cb0ba7'
  }
  stages {
    stage('Build') {
//       when {
//         not {
//           branch 'master'
//         }
//       }
      steps {
        snApplyChanges(appScope: "APPSCOPE", branchName: "${BRANCH}", url: "${DEVENV}", credentialsId: "${CREDENTIALS}")
      }
    }
    stage('Test') {
//       when {
//         not {
//           branch 'master'
//         }
//       }
      steps {
        snApplyChanges(appScope: "APPSCOPE", branchName: "${BRANCH}", url: "${TESTENV}", credentialsId: "${CREDENTIALS}")
        snRunTestSuite(credentialsId: "${CREDENTIALS}", url: "${TESTENV}", testSuiteSysId: "${TESTSUITEID}", withResults: true)
      }
    }
  }
}
