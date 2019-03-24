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
        catchError()
      }
    }
    stage('promote?') {
      steps {
        emailext(subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS', body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:  Check console output at $BUILD_URL to view the results.', replyTo: 'wilberncarey@hotmail.com', to: 'wilberncarey@hotmail.com', from: 'wilberncarey@hotmail.com', mimeType: 'text/html')
        echo 'HELLO'
        input(message: 'would you like to make a snapshot', id: 'snapshot', ok: 'yes', submitter: 'will')
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