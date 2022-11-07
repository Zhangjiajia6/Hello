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
                if(${BUILD_LOG}.contains("java")){
                    sh "echo YES it's JAVA"
                }
            }
        }
    }
}
