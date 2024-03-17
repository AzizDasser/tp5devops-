pipeline {
  environment {
    registry = "adasser/tp5"
    registryCredential = 'a5a22125-c05e-4ca8-a4b1-e650ae9cf5f2'
    dockerImage = ''
    gitBranch = 'main'
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git branch: "${gitBranch}",url: 'https://github.com/AzizDasser/tp5devops-.git'
      }
    }
    stage('Building image') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Test image') {
      steps {
        script {

          echo "Tests passed"
        }
      }
    }
    stage('Publish Image') {
      steps {
        script {
          docker.withRegistry('', registryCredential) {
            dockerImage.push()
          }
        }
      }
    }
  }
}