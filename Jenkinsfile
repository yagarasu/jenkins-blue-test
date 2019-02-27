pipeline {
  agent any
  stages {
    stage('Setup') {
      steps {
        sh 'yarn install'
      }
    }
    stage('Test') {
      steps {
        sh 'CI=true yarn test'
        sh 'CI=true yarn coverage'
      }
      post {
        always {
          step([$class: 'CoberturaPublisher', coberturaReportFile: 'coverage/cobertura-coverage.xml'])
        }
      }
    }
    stage('Build') {
      steps {
        sh 'CI=true yarn build'
      }
    }
    stage('Deploy') {
      when {
        expression {
          currentBuild.result == null || currentBuild.result == 'SUCCESS'
        }
      }
      steps {
        echo 'Deploy!'
      }
    }
  }  
}

