pipeline {
  agent none
  stages {
    stage('build') {
      agent any
      steps {
        sleep 2
        sleep 123
      }
    }
    stage('dev deploy') {
      steps {
        catchError() {
          input(message: 'approve', id: 'approve', ok: 'YES', submitter: 'dmin', submitterParameter: 'YES')
        }

      }
    }
    stage('promote?') {
      parallel {
        stage('promote?') {
          steps {
            echo 'Move to Snapshot'
            input(message: 'Crete Snapshot', id: 'Deploy Snapshot to Nexus?', ok: 'Deploy Snapshot to Nexus', submitter: 'will', submitterParameter: 'snapshot')
          }
        }
        stage('Deploy to Test?') {
          steps {
            input(message: 'Deploy to Test?', id: 'Deploy to Test?', ok: 'Deploy to Test?', submitter: 'will', submitterParameter: 'version')
          }
        }
      }
    }
    stage('test deploy') {
      steps {
        echo 'new'
      }
    }
    stage('Release?') {
      steps {
        echo 'release'
      }
    }
    stage('QA deploy') {
      steps {
        echo 'next'
      }
    }
    stage('Promote?') {
      steps {
        echo 'next'
      }
    }
  }
}