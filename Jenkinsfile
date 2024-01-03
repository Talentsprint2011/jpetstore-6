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

    stage('Unit Test') {
      steps {
        sh './mvnw test'
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''./mvnw clean verify sonar:sonar \\
  -Dsonar.projectKey=JPetstore \\
  -Dsonar.projectName=\'JPetstore\' \\
  -Dsonar.host.url=http://172.31.33.214:9000 \\
  -Dsonar.token=sqp_71d08155437337b9daf2277154c6104712cf6421'''
      }
    }

  }
}