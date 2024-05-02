pipeline {
  agent any
  triggers{
    pollSCM('H/2 * * * *')
  }
  stages {
   stage('Build Application') {
      steps {
        sh 'mvn clean install'
      }  
    }
    stage('Deploy CloudHub') {
      environment {
        ANYPOINT_CREDENTIALS = credentials('f2ec664c-f2dc-42c9-84c5-f34d7272184d')
      }
      steps {
        sh "mvn deploy -DmuleDeploy -Dcloud.env=Sandbox -DcloudhubAppName=account-api-raml -Dmule.version=4.6.1 -Dcloud.user=raou -Dcloud.password=${ANYPOINT_CREDENTIALS_PSW}"
      }
    }
  }
}
