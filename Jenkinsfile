pipeline {

    tools {
            maven 'maven'
            nodejs "NodeJS"         
          }

    environment {

     springF="Achat_back"   
     angularF="Achat_front"    
   }

          agent any

    stages{



                  stage('Sonarqube') { 
                steps { 
                  
                   sh '''
                  
                  cd ${springF} &&  mvn sonar:sonar \
                 -Dsonar.projectKey=achat_proj \
                 -Dsonar.projectName=achat_proj \
                 -Dsonar.host.url=http://192.168.1.78:9000 \
                 -Dsonar.login=cef4c391ef7d4eb31975f3b6de847a8184e57cb7

                     '''

                       }

            }


              



           



    }
}