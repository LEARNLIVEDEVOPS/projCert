pipeline {

  agent any

  stages {
    stage ('Clone Repo') {
            steps {
                /* Clone git Repository */
                checkout scm
                   }
                              }

    stage("build") {

      steps {

        sh """

          docker build -t ramkitcs/phpapp .

        """

      }

    }

    stage("run") {

      steps {

        sh """

          docker run -d -p 8081:80 ramkitcs/phpapp

        """

      }

    }

  }
}
