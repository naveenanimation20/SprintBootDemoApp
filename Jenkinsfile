pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn install'
      }
    }

    stage('Unit Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Deployement') {
      steps {
        sh 'mvn spring-boot:run '
        build job: 'Jan2020POMSeries'
      }
    }

  }
  tools {
    maven 'M3'
  }
}
