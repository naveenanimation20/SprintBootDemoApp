pipeline {
  agent any
  stages {
    
    stage('Build') {
      parallel {
        
        //1
        stage('Build') {
          steps {
            sh 'mvn install'
            sh 'mvn spring-boot:run'
          }
        }

        //2
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
