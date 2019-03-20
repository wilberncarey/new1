pipeline {
  agent none
  stages {
    stage('build') milestone() {
      agent any
      steps {
        sleep 2
      }
 lock(resource: 'myResource', inversePrecedence: true)
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
