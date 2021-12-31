pipeline {
  agent any
  environment {
    APPSYSID = '0f94aa8a8760011088f3ca280cbb357b'
    APPSCOPE = 'x_666176_github_ci'
    BRANCH = "${BRANCH_NAME}"
    CREDENTIALS = '2934736d-facb-4169-a459-01f7119eddee'
    DEVENV = 'https://dev117906.service-now.com/'
    TESTENV = 'https://dev99253.service-now.com/'
    TESTSUITEID = '1ac870858738011088f3ca280cbb3525'
  }
  stages {
    stage('Dev') {
      when {
        branch 'dev'
      }
      steps {
        echo "${BRANCH}"
        snApplyChanges(appScope: "${APPSCOPE}", branchName: "${BRANCH}", url: "${DEVENV}", credentialsId: "${CREDENTIALS}")
        snRunTestSuite(credentialsId: "${CREDENTIALS}", url: "${DEVENV}", testSuiteSysId: "${TESTSUITEID}", withResults: true)
      }
    }
    stage('Test') {
      when {
        branch 'test'
      }
      steps {
        echo "${BRANCH}"
        snApplyChanges(appScope: "${APPSCOPE}", branchName: "${BRANCH}", url: "${TESTENV}", credentialsId: "${CREDENTIALS}")
        snRunTestSuite(credentialsId: "${CREDENTIALS}", url: "${TESTENV}", testSuiteSysId: "${TESTSUITEID}", withResults: true)
      }
    }
  }
}
