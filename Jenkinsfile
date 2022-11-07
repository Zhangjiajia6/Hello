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
            if(log.contains("1.8.0_322")){
                sh 'echo YES 1.8.0_322 version JAVA'
            }
        }
    }
}
