pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Say Hello') {
      steps {
        echo "Hello ${params.Name}!"
        sh 'java -version'
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
      }
    }
//    stage('Deploy')
//    {
//      options {
//        timeout(time: 30, unit: 'SECONDS') 
//      }
//      input {
//        message "Which Version?"
//        ok "Deploy"
//        parameters {
//            choice(name: 'APP_VERSION', choices: "v1.1\nv1.2\nv1.3", description: 'What to deploy?')
//        }
//      }
//      steps {
//        echo "Deploying ${APP_VERSION}."
//      }
//    }
//  }
//      stage('Get Kernel') {
//      steps {
//        script {
//          try {
//            KERNEL_VERSION = sh (script: "uname -r", returnStdout: true)
//          } catch(err) {
//           echo "CAUGHT ERROR: ${err}"
//            throw err
//          }
//        }
//      }
//    stage('Say Kernel') {
//      steps {
//        echo "${KERNEL_VERSION}"
//      }
//    }
      stage('Testing') {
        failFast true
        parallel {
          stage('Java 8') {
            agent { label 'jdk8' }
            steps {
              sh 'java -version'
              sleep time: 10, unit: 'SECONDS'
            }
          }
          stage('Java 9') {
            agent { label 'jdk9' }
            steps {
              sh 'java -version'
              sleep time: 20, unit: 'SECONDS'
            }
          }
        }
      }
  }
      environment {
    MY_NAME = 'Jeff'
    TEST_USER = credentials('test-user')
  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
  post {
    aborted {
      echo 'Why didn\'t you push my button?'
    }
  }
}
