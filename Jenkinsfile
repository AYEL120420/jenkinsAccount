pipeline {
  agent any
  triggers{
    pollSCM('H/2 * * * *')
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
            echo 'Deploying mule project due to the latest code commit…' 
            echo 'Deploying to the configured environment….' 
            sh 'mvn clean deploy -DmuleDeploy  
            -DcloudhubAppName=account-api 
            -Dmule.version=4.6.1
            -Dusername=${ANYPOINT_CREDENTIALS_USR} -
            Dpassword=${ANYPOINT_CREDENTIALS_PSW} 
            -DworkerType=Micro -Dworkers=1' 
            }  
    }
  }
}