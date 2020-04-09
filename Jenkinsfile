pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        

        stage('Build') {
          steps {
            sh 'mvn install'
            sh 'mvn spring-boot:run'
          }
        }

      }
    }

    stage('reports') {
      steps {
        script {
          allure([
            includeProperties: false,
            jdk: '',
            properties: [],
            reportBuildPolicy: 'ALWAYS',
            results: [[path: '/allure-results']]
          ])


          // publish html
          publishHTML([
            allowMissing: false,
            alwaysLinkToLastBuild: false,
            keepAll: false,
            reportDir: 'build',
            reportFiles: 'TestExecutionReport.html',
            reportName: 'Extent HTML Report',
            reportTitles: ''
          ])
        }

      }
    }

  }
  tools {
    maven 'M3'
  }
}
