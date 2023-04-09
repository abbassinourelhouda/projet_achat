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



    }
}