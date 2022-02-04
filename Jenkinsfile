pipeline {
  properties([
    parameters([
        choice(choices: 'sprint_6\nsprint_7\nsprint_8\nSprint_9', description: 'Select branch to Build', name: 'Branch'),
        choice(choices: 'No\nYes', , name: 'choice2'),
        choice(choices: 'No\nYes', name: 'choice3')
    ])
  ])

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