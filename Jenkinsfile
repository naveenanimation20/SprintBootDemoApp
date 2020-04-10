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
        sh 'mvn spring-boot:run'
      }
    }

    stage('UI Test') {
      steps {
        git(url: 'https://github.com/naveenanimation20/Jan2020POMSeries', branch: 'master', changelog: true)
        sh 'mvn test -Denv=qa -Dbrowser=firefox'
      }
    }

  }
  tools {
    maven 'M3'
  }
}