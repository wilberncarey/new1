pipeline {
  agent none
  stages {
    stage('build'){
      agent any
      steps {
        sleep 2
      }
    }
    stage('approval') milestone() {
      steps {
        catchError() {
          input(message: 'approve', id: 'approve', ok: 'YES', submitter: 'dmin', submitterParameter: 'YES')
        }

      }
    }
  }
}
