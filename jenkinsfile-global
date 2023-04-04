pipeline {

    tools {
            maven 'maven'
            nodejs "NodeJS 16.3"         
          }

    environment {

     springF="Achat_back"   
     angularF="Achat_front"    
   }

          agent any

    stages{

            // stage('Cleaning and install ') {

            //     steps {

            //     sh ' cd ${springF} && mvn clean install'

            //     }
            // }

            // stage('build ') {

            //     steps {

            //     sh ' cd ${angularF} && npm install '

            //     sh ' cd ${angularF} && ng build '

            //     }
            // }

            stage('Compiling..') {

                steps {

                sh 'cd ${springF} && mvn compile'
                
                 }
             }


        //     stage('Sonarqube') { 
        //         steps { 
                  
        //           sh '''
                  
        //          cd ${springF} &&  mvn sonar:sonar \
        //         -Dsonar.projectKey=achat_proj \
        //         -Dsonar.projectName=achat_proj \
        //         -Dsonar.host.url=http://192.168.2.78:9000 \
        //         -Dsonar.login=4425020259dcc2fa1edfccad638acd88ecc8f7cc

        //             '''

        //               }

        //    }

        //    stage('Nexus') {

        //         steps {
                    
        //           script {
                   
        //            nexusArtifactUploader artifacts: 
        //            [
                    
        //                   [
        //               artifactId: 'tpAchatProject',
        //               classifier: '',
        //               file: 'Achat_back/target/tpAchatProject-1.0.jar',
        //               type: 'jar'
                      
        //                   ]
                      
        //            ],
                   
        //           pom: 'Achat_back/pom.xml', 
        //           credentialsId: 'nexus_cred',
        //           groupId: 'com.esprit.examen',
        //           nexusUrl: '192.168.2.78:8081',
        //           nexusVersion: 'nexus3',
        //           protocol: 'http',
        //           repository: 'achat_app',
        //           version: '1.0'

        //           }
                
        //               }

        //     }



     


        //     stage('Testing..') {
        //         steps {
        //         sh 'cd ${springF} && mvn test'
        //     }
        // }



            // stage('MVN SONARQUBE')
            // {
            //     steps{
            //     sh 'cd ${springF} && mvn sonar:sonar -Dsonar.login=*** -Dsonar.password=***'
            //     }
            // }



            //  stage("Nexus deploy"){
            //     steps{
            //          script{
            //             nexusArtifactUploader artifacts: [[artifactId: 'achat', classifier: '', file: 'achat_back/target/achat-1.0.jar', type: 'jar']], credentialsId: '***', groupId: 'tn.esprit.rh', nexusUrl: 'ip***:8081', nexusVersion: 'nexus3', protocol: 'http', repository: '***', version: '1.0'
            //          }
            //         }

            //     }




    //         stage("build and push back/front images"){
    //     steps{
    //         script {
            
    //         echo "====++++executing build and push back + front images++++===="
    
    //      withCredentials([usernamePassword(credentialsId: '***', passwordVariable: 'PASS', usernameVariable: 'USER')]){
         
    //                         sh "docker build -t $USER/achat_back ${springF}/"

    //                         sh "docker build -t $USER/achat_front ${angularF}/"

    //                         sh "echo $PASS | docker login -u $USER --password-stdin"

    //                         sh "docker push $USER/achat_back"

    //                         sh "docker push $USER/achat_front"
    //                     }
    //     }
    //     }
    //     post{

    //         always{
    //             sh "docker logout"
    //         }
        
    //         success{
    //             echo "====++++push image execution failed++++===="
    //         }
        
    //         failure{
    //             echo "====++++push image execution failed++++===="
    //         }
    
    //     }
    // }




    //        stage('Deploy App'){

    //         steps {

    //         sh 'docker-compose -f docker-compose.yml up  -d'
    //          }

    //         post{
        
    //         success{
    //             echo "====++++Success++++===="
    //         }
        
    //         failure{
    //             echo "====++++Failed++++===="
    //         }
    
    //     }
                    

    //       }


    }
}