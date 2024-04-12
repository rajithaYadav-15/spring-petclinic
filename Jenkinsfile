pipeline {
    agent any
    tools { 
        maven 'MAVEN_HOME'
    }
    stages {
        stage('Build') {
            steps {
                mail bcc: '', body: 'Build Started', cc: '', from: '', replyTo: '', subject: 'Build Started', to: 'jenkinsamplesmtp@gmail.com'
                sh 'mvn clean package'
                archiveArtifacts artifacts: '**/spring-petclinic-*.jar'
                junit stdioRetention: '', testResults: '**/surefire-reports/*.xml'
                mail bcc: '', body: 'Build completed', cc: '', from: '', replyTo: '', subject: 'Build completed', to: 'jenkinsamplesmtp@gmail.com'
            }
        }
    }
}
