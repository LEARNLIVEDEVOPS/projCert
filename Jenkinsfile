#!/bin/groovy
def dockerImg
pipeline {
        // environment {
         //registry = "ramkitcs/phpapp"
          //RegistryCredential = 'ramkitcs'
           //dockerImage = ' '
//}
    agent any
   stages {
         stage ('Clone Repo') {
            steps {
                /* Clone git Repository */
                checkout scm
                   }
                              }
         stage ('Build Image') {
            steps {
                echo "Build docker image"
                 script {
                    /* This builds the actual image; synonymous to
                    * docker build on the command line */
                  //  sh "sudo docker build -t ramkitcs/phpapp ."
                docker.build("ramkitcs/phpapp:${env.BUILD_NUMBER}")
                         //dockerImg = docker.build("ramkitcs/phpapp")
                }
            }
        }
stage ('Push Image') {
     steps  {
          echo "Push Image on DockerHub"
          //script {
            //        docker.withRegistry('https://registry.hub.docker.com', 'ramkitcs') {
              //      dockerImg.push("ramkitcs/phpapp")
//}
//}
}
}
stage ('Deploy') {
     steps {
         echo "Run containers"
         script {
          sh "sudo docker run -d -p 8084:80 ramkitcs/phpapp"
                     }
                  }
  }           
} 
}
