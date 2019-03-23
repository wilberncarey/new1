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
            emailext(subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS', body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:  Check console output at $BUILD_URL to view the results.', replyTo: 'wilberncarey@hotmail.com', to: 'wilberncarey@hotmail.com', from: 'wilberncarey@hotmail.com')
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
        echo 'hello'
        input(message: 'forwrd', id: 'forwrd', submitter: 'will', submitterParameter: 'will', ok: 'deploy?')
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