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
                if(log.contains("java")){
                    sh 'echo YES it's JAVA'
                }
            }
        }
    }
}
