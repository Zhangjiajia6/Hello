pipeline {
    parameters {
        string(name: 'NOTIFICATION_EMAIL', defaultValue: 'jiajia.zhang@intel.com', trim: true,
               description: 'Who wants to receive the execution results ?')
    }
    agent any
    stages {
        stage('build') {
            steps {
                sh 'java --version'
            }
        }
        stage('Check Log') {
            steps {
            catchError(stageResult: 'FAILURE') {
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
    }
    post {
        failure {
            emailext (
                mimeType: 'text/html',
                subject: '[Jenkins Pipeline]-> ' + currentBuild.fullDisplayName,
                from: 'Jenkins.Pipeline.Data.Post-process',
                to: params.NOTIFICATION_EMAIL,
                body: '${SCRIPT, template="groovy-html.template"}',
                attachLog: true
            )
        }
    }
}
