pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'This is the build stage of the code'
          }
        }

        stage('Build/Shell Script') {
          steps {
            sh './mvnw clean compile'
          }
        }

      }
    }

  }
}