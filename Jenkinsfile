pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                mail bcc: '', body: 'Build Started', cc: '', from: '', replyTo: '', subject: 'Build Started', to: 'jenkinsamplesmtp@gmail.com'
                tool name: 'MAVEN_HOME', type: 'maven'
                sh 'mvn clean package'
                archiveArtifacts artifacts: '**/spring-petclinic-*.jar'
                junit stdioRetention: '', testResults: '**/surefire-reports/*.xml'
                mail bcc: '', body: 'Build completed', cc: '', from: '', replyTo: '', subject: 'Build completed', to: 'jenkinsamplesmtp@gmail.com'
            }
        }
    }
}
