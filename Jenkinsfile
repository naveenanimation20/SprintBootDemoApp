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

      }
    }

    

  }
  tools {
    maven 'M3'
  }
}
