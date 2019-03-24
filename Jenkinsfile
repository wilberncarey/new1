pipeline {
  agent none
  stages {
    stage('build') {
      agent any
      steps {
        sleep 2
      }
    }
    stage('Create Snapshot?') {
      agent any
      steps {
        emailext(subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS', body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS.<br/> <br/> Check console <a href="$BUILD_URL">output</a> to view full results.<br/> If you cannot connect to the build server, check the attached logs.<br/> <br/> --<br/> Following is the last 100 lines of the log.<br/> <br/> --LOG-BEGIN--<br/>', replyTo: 'wilberncarey@hotmail.com', to: 'wilberncarey@hotmail.com', from: 'wilberncarey@hotmail.com', mimeType: 'text/html')
        echo 'HELLO'
        input(message: 'would you like to make a snapshot', id: 'snapshot', ok: 'yes', submitter: 'will')
      }
    }
    stage('dev deploy') {
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