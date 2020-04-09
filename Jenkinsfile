pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh 'mvn install'
            sh 'mvn spring-boot:run'
          }
        }

        stage('test') {
          steps {
            sh 'mvn test'
          }
        }

      }
    }

  }
  tools {
    maven 'M3'
  }
}