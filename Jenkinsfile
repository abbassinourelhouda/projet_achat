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

// teeeeest 10/04


      
           // stage('Création d image back "livrable dans dockerfile"') {

             //    steps {

             //    sh ' cd ${springF} && docker build -t achat_back_2 .'

              //   }
            // }

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
                   repository: 'achat_proj',
                   version: '1.0'

                   }
                
                       }

            }






           



    }
}