pipeline {

  agent {
    docker {
      image 'node:16.13.0-alpine'
      args '-u root'
    }
  }
  stages {
    stage('print env') {
      steps {
        sh 'printenv'
      }
    }
  }
  post {
    success {
        slackSend   color: 'good',
                    message: "build success."
    }
    failure {
        slackSend   color: 'danger',
                    message: "build failure."
        }
    }

}