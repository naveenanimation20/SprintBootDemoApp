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

    stage('Deployment') {
      parallel {
        stage('Deployment') {
          steps {
            sh 'mvn spring-boot:run'
          }
        }

        stage('Server Check') {
          steps {
            sh '''#!/bin/bash
status=0
successStatus=1 
code=200
while [ $status != $successStatus ]; do
  httpCode=$(curl -s --head -w %{http_code} http://localhost:3456 -o /dev/null)
  if [ $httpCode -eq $code ]; then
    echo "url worked"
    status=1
  else
  	echo "url not working yet"
  	sleep 20
  fi
done'''
          }
        }

      }
    }

  }
  tools {
    maven 'M3'
  }
}