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

      stage('Start MySQL') {


                steps {
                    // Démarrer une instance de MySQL
                    sh 'docker run -d -p 3306:3306 --name mysqldb-test  -e MYSQL_ROOT_PASSWORD=nour123 -e MYSQL_DATABASE=tpachato mysql'
                }
                }


      
           // stage('Création d image back "livrable dans dockerfile"') {

             //    steps {

             //    sh ' cd ${springF} && docker build -t achat_back_2 .'

              //   }
            //        


              stage('Création de .jar ') {

                  steps {

                     sh ' cd ${springF} && mvn clean install -DskipTests'

                              }
                         
              }


              stage('Test unitaire & mock produit') {
                steps {
                    // Étape de test unitaire
                    sh 'cd ${springF} && mvn test'
                }
               
                }

            stage('Stop MySQL') {
                steps {
                    // Arrêter l'instance de MySQL
                    sh 'docker stop mysqldb-test && docker rm mysqldb-test'
                }
                }
      
    }

}