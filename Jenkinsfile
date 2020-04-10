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
            sh '''commande () {
	    curl -X GET \\
	         
	         -d@- \\
	         http://127.0.0.1:3456 <<EOF
	    
	EOF
	}'''
            }
          }

        }
      }

    }
    tools {
      maven 'M3'
    }
  }