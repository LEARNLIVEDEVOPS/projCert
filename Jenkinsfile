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
          sh "docker build -t ramktcs/phpapp-3 ."
        }
      }
    }


  }
}
