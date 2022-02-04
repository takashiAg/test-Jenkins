pipeline {
  parameters {
    string(name: 'MY_PARAM', defaultValue: '', description: 'My parameter')
  }
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