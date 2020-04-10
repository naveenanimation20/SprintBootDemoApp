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

        stage('') {
          steps {
            sh '''TEST="curl http://127.0.0.1:3456
echo $TEST

RESPONSE=`$TEST`
echo $RESPONSE'''
          }
        }

      }
    }

  }
  tools {
    maven 'M3'
  }
}