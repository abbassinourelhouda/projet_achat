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

    stages {
  
                // Démarrer une instance de MySQL pour les tests
             stage('Start MySQL') {

                steps {
                    sh 'docker run -d -p 3306:3306 --name mysqldb-test  -e MYSQL_ROOT_PASSWORD=nour123 -e MYSQL_DATABASE=tpachato mysql'
                }
                }

               // Stage: Création de livrable pour spring:back
              stage('Création de .jar ') {

                  steps {

                     sh ' cd ${springF} && mvn clean install -DskipTests'

                              }
                         
              }

               // Stage: Création de /dist pour angular:front
               stage('Création de dist') {

                 steps {

                 sh ' cd ${angularF} && npm install'

                 sh ' cd ${angularF} && ng build'

                 }
             }


             // Lancement de test unitaire + mock pour l'entité produit
              stage('Test unitaire & mock produit') {
                steps {

                    sh 'cd ${springF} && mvn test'
                }
               
                }

            // Arrêter l'instance de MySQL pour les tests
            stage('Stop et suppression de MySQL') {

                steps {
                    sh 'docker stop mysqldb-test && docker rm mysqldb-test'
                }
                }
          
           // Lancer le test de qualité du code (sonarqube)
            stage('Sonarqube') { 
                steps { 
                  
                   sh '''
                  
                  cd ${springF} &&  mvn sonar:sonar \
                 -Dsonar.projectKey=achat_proj \
                 -Dsonar.projectName=achat_proj \
                 -Dsonar.host.url=http://192.168.1.78:9000 \
                 -Dsonar.login=97009a5ab57963154d8db1121d12e470807eec21

                     '''

                       }

            }
          
         // Déposer le livrable sur Nexus
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
          
          // Build de l’image (spring + angular) +   Déposer les deux images sur DockerHub
          stage("build and push back/front images"){
         
         
                 steps{

                    script {
            
             echo "====++++executing build and push back + front images++++===="
    
          withCredentials([usernamePassword(credentialsId: 'dockerhub_cred', passwordVariable: 'PASS', usernameVariable: 'USER')]){
         
                             sh "docker build -t $USER/achat_back ${springF}/"

                             sh "docker build -t $USER/achat_front ${angularF}/"

                             sh "echo $PASS | docker login -u $USER --password-stdin"

                             sh "docker push $USER/achat_back"

                             sh "docker push $USER/achat_front"
                         }
                 }
            }
         post{

             always{
                 sh "docker logout"
             }
        
             success{
                 echo "====++++push image execution success++++===="
             }
        
             failure{
                 echo "====++++push image execution failed++++===="
             }
    
            }

          }
          // Création du livrable Spring à partir du fichier DockerFile
           //stage('Création d image back "livrable dans dockerfile"') {

             //    steps {

               //  sh ' cd ${springF}/dockerfile2/ && docker build -t achat_back_2 .'

                 //}
           //}
        
          // Lancer simultanément en utilisant docker-compose (spring+angular+mysql+phpmyadmin)
          stage('run docker-compose'){

                 steps {

                sh 'docker-compose -f docker-compose.yml up  -d'
                    }

             post{
        
             success{
                 echo "====++++Success++++===="
             }
        
             failure{
                 echo "====++++Failed++++===="
               }
    
           }
    
  
             }
      }


    }

