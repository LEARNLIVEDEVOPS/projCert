pipeline {

  agent any

  stages {
    
    //Github Checkout
    
     stage ('Clone Repo') {
            steps {
                /* Clone git Repository */
                checkout scm
                   }
                              }

    //Docker Image Building
    
     stage('Building image') {
        steps{
          script {
              sh "docker build -t ramktcs/phpapp-3 ."
        }
      }
    }

    //Docker Image push to Dockerhub
    
   stage ('Push Image') {
     steps  {
          echo "Push Image on DockerHub"
          script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                    sh "docker push ramkitcs/phpapp-3"
}
}
}
    
      //Docker Image deployment
    
    stage ('Deploy') {
     steps {
         echo "Run containers"
         script {
          sh "sudo docker run -itd -p 8081:80 ramkitcs/phpapp-3"
                     }
                  }
  }          
    

  }
}
