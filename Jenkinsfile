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
      parallel {
        stage('Deployement') {
          steps {
            sh 'mvn spring-boot:run '
          }
        }

        stage('UI Test') {
          steps {
            sh '''#!/bin/bash

int status = sh(script: "curl -sLI -w \'%{http_code}\' $url -o http://127.0.0.1:3456", returnStdout: true)


echo status'''
          }
        }

      }
    }

  }
  tools {
    maven 'M3'
  }
}