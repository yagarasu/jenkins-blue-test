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
      }
    }
    stage('Build') {
      steps {
        sh 'CI=true yarn build'
      }
    }
  }
}

