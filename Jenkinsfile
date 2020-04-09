pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn install'
      }
    }
    
    stage('Deploye') {
      steps {
        sh 'mvn spring-boot:run'
      }
    }

    stage('test') {
      steps {
        sh 'mvn test'
      }
    }

  }
  tools {
    maven 'M3'
  }
}
