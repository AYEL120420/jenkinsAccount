pipeline {
  agent any
  triggers{
    pollSCM('H/2 * * * *')
  }
      environment {
        // Define environment variables using credentials stored in Jenkins
        CLOUD_USER = credentials('jenkins-cloud-user')
        CLOUD_PASSWORD = credentials('jenkins-cloud-password')
    }
  stages {
   stage('Build Application') {
      steps {
        sh 'mvn clean install -X'
      }  
    }
    stage('Deploy CloudHub') {
      environment {
        ANYPOINT_CREDENTIALS = credentials('f2ec664c-f2dc-42c9-84c5-f34d7272184d')
      }
      steps {
sh 'mvn deploy -DmuleDeploy -Dcloud.env=Sandbox -DcloudhubAppName=account-api-raml -Dmule.version=4.6.1 -Dcloud.user=$CLOUD_USER -Dcloud.password=$CLOUD_PASSWORD'
      }
    }
  }
}