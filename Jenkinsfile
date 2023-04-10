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

// teeeeest

      stage('Nexus') {

                 steps {
                    
                   script {
                   
                    nexusArtifactUploader artifacts: 
                    [
                    
                           [
                       artifactId: 'tpAchatProject',
                       classifier: '',
                       file: 'Achat_back/target/tpAchatProject-1.0.jar',
                       type: 'jar'
                      
                           ]
                      
                    ],
                   
                   pom: 'Achat_back/pom.xml', 
                   credentialsId: 'nexus_cred',
                   groupId: 'com.esprit.examen',
                   nexusUrl: '192.168.1.78:8081',
                   nexusVersion: 'nexus3',
                   protocol: 'http',
                   repository: 'achat_app',
                   version: '1.0'

                   }
                
                       }

            }






           



    }
}