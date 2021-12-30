// Simple script with one step: apply changes from source control linked to the app repo

pipeline {
    agent any

    stages {
        stage('preparation') {
            steps {
                snApplyChanges url: "https://dev99253.service-now.com", credentialsId: "2934736d-facb-4169-a459-01f7119eddee", appScope: "x_666176_github_ci"
            }
        }
    }
}
