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
            sh '''echo -n "Waiting"
while true; do
        STATUS_CODE=`curl -X GET http://localhost:3456`
        if [[ $STATUS_CODE -eq 404 ]]; then
                echo -n "."
                sleep 2
        else
                break
        fi
done
echo ""'''
          }
        }

      }
    }

  }
  tools {
    maven 'M3'
  }
}