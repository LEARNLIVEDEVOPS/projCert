#!/bin/groovy
def dockerImg
pipeline {
        environment {
         registry = "ramkitcs/phpapp"
          RegistryCredential = 'ramkitcs'
           dockerImage = ' '
}
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
                    dockerImg = docker.build("ramkitcs/phpapp")
                }
            }
        }
stage (‘Push Image’) {
     Steps  {
          Echo “Push Image on DockerHub”
          Script {
                    docker.withRegistry('https://registry.hub.docker.com', 'ramkitcs') {
                    dockerImg.push(“$(env.BUILD_NUMBER)”)
                     dockerImg.push(“latest”)

}
}
}
}
stage (‘Deploy’) {
     Steps {
         echo “Run containers”
         Script {
          Sh “sudo docker run -itd container-$BUILD_NUMBER -p 8084:80 ramkitcs/phpapp:$(env.BUILD_NUMBER)”
                     }
                  }
  }           
} 
