pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn install'
      }
    }
    
    stage('SonarQube Test') {
            steps {
              echo 'Initiating SonarQube test'
              sh 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dlicense.skip=true'
              echo 'SonarQube test Complete'
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

        stage('Functional Test') {
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
          done

          echo "status is:"
          echo $status

              if [ $status -eq $successStatus ]; then
                 echo "UI test running"
                 mvn test
              else
                 echo "UI test not running"
               fi'''
          }
        }
        
        
        stage("speak") {
          steps{
             slackSend color: '#BADA55', message: 'Build and Deployment is successfully done', channel: 'general'
          }
        }
        

      }
      
    }

  }
  tools {
    maven 'M3'
  }
}
