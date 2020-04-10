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

    stage('UI Test Pipeline') {
      steps {
        build 'Jan2020POMSeries'
      }
    }

  }
  tools {
    maven 'M3'
  }
}