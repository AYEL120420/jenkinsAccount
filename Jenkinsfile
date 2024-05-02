pipeline{  
    agent any 
        stages{ 
            stage('Build Application') { 
                steps { 
                bat 'mvn clean install' 
                } 
        } 
            stage('Deploy CloudHubs') { 
            environment { 
            ANYPOINT_CREDENTIALS = credentials('f2ec664c-f2dc-42c9-84c5-f34d7272184d') 
            } 
        steps { 
        echo 'Deploying mule project due to the latest code commit…' 
        echo 'Deploying to the configured environment….' 
        bat 'mvn clean deploy -DmuleDeploy  
        -Dusername=${ANYPOINT_CREDENTIALS_USR} -
        Dpassword=${ANYPOINT_CREDENTIALS_PSW} 
        -DworkerType=Micro -Dworkers=1' 
        }  
        } 
     } 
}