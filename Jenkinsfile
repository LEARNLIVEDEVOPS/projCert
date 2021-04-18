pipeline {

  agent any

  stages {
    stage ('Clone Repo') {
            steps {
                /* Clone git Repository */
                checkout scm
                   }
                              }

 
 stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry
        }
      }
    }


  }
}
