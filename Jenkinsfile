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


             stage('Création de .jar ') {

                 steps {

                 sh ' cd ${springF} && mvn clean install'

                 }
             }

             stage('Création de dist') {

                 steps {

                 sh ' cd ${angularF} && npm install'

                 sh ' cd ${angularF} && ng build'

                 }
             }


    }
}