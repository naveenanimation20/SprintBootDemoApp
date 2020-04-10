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
            sh '''response=$(curl -s -o /dev/null -w "%{http_code}\\n" http://127.0.0.1:3456)
echo response
if [ "$response" != "200" ]
then
 exit 1
fi'''
          }
        }

      }
    }

  }
  tools {
    maven 'M3'
  }
}