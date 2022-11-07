pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'java --version'
            }
        }
    }
    post {
        always {
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
