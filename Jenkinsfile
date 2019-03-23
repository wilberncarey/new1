pipeline {
  agent none
  stages {
    stage('build') {
      agent any
      steps {
        sleep 2
      }
    }
    stage('dev deploy') {
      steps {
        catchError() {
          input(message: 'approve', id: 'approve', ok: 'YES', submitter: 'dmin', submitterParameter: 'YES')
        }

      }
    }
    stage('promote test?') {
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
        emailext(subject: 'approve', body: 'please approve', attachLog: true, attachmentsPattern: 'wil', from: 'will', replyTo: 'wbc12203@gmail.com', to: 'wbc12203@gmail.com')
        mail(subject: 'test', body: 'test', from: 'wbc12203@gmail.com', replyTo: 'wbc12203@gmail.com', to: 'wbc12203@gmail.com')
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