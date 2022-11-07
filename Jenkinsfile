pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'java --version'
            }
        }
        stage('Check Log') {
            catchError {
                script {
                    if(manager.logContains(".*JAVA.*")){
                        echo "YES it's JAVA"
                    } else {
                        error("No logs contains java")
                    }
                }
            }
        }
    }
    post {
        failure {
            emailext body: 'this is a test', subject: 'Pipeline Fail test', to: 'jiajia.zhang@intel.com'
        }
    }
}
