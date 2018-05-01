pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Say ${MY_NAME}') {
      steps {
        echo 'Hello World!'
        sh 'java -version'
      }
    }
  }
  environment {
    MY_NAME = 'Jeff'
  }
}