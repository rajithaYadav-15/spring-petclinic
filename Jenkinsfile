pipeline {
    agent any
    tools { 
        maven 'MAVEN_HOME'
    }
    parameters {
    choice(
        name: 'MAVEN_GOALS',
        choices: ['package','clean package'],
        description: 'maven goals' )
  }
    stages {
        stage('Build') {
            steps {
                mail bcc: '', body: 'Build Started', cc: '', from: '', replyTo: '', subject: 'Build Started', to: 'jenkinsamplesmtp@gmail.com'
                sh "mvn ${params.MAVEN_GOALS}"
                archiveArtifacts artifacts: '**/spring-petclinic-*.jar'
                junit stdioRetention: '', testResults: '**/surefire-reports/*.xml'
                mail bcc: '', body: 'Build completed', cc: '', from: '', replyTo: '', subject: 'Build completed', to: 'jenkinsamplesmtp@gmail.com'
            }
            post {
              failure {
                  mail bcc: '',
                       from: 'jenkins@com',
                       to: 'jenkinsamplesmtp@gmail.com',
                       subject: "Build of ${JOB_BASE_NAME} with Build id ${BUILD_ID} is failed",
                       body: "Refer to ${RUN_DISPLAY_URL} for more info"
                  }
              success {
                  mail bcc: '',
                       from: 'jenkins@com',
                       to: 'jenkinsamplesmtp@gmail.com',
                       subject: "Build of ${JOB_BASE_NAME} with Build id ${BUILD_ID} is success",
                       body: "Refer to ${RUN_DISPLAY_URL} for more info"
                }
            }
        }
    }
}
