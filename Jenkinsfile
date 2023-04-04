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

             stage('Get project from GIT'){
                steps{
                    echo 'Pulling...';
                    git branch: 'main',
                    url : 'https://github.com/abbassinourelhouda/projet_achat.git';
                }
            }

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


    }
}