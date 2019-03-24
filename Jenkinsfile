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
        emailext(subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS', body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS.<br/> <br/> Check console <a href="${BUILD_URL}/input">output</a> to view full results.<br/> If you cannot connect to the build server, check the attached logs.<br/> <br/> --<br/> Following is the last 100 lines of the log.<br/> <br/> --LOG-BEGIN--<br/> <pre style=\'line-height: 22px; display: block; color: #333; font-family: Monaco,Menlo,Consolas,"Courier New",monospace; padding: 10.5px; margin: 0 0 11px; font-size: 13px; word-break: break-all; word-wrap: break-word; white-space: pre-wrap; background-color: #f5f5f5; border: 1px solid #ccc; border: 1px solid rgba(0,0,0,.15); -webkit-border-radius: 4px; -moz-border-radius: 4px; border-radius: 4px;\'> ${BUILD_LOG, maxLines=100, escapeHtml=true} </pre> --LOG-END--', replyTo: 'wilberncarey@hotmail.com', to: 'wilberncarey@hotmail.com', from: 'wilberncarey@hotmail.com', mimeType: 'text/html')
        echo 'HELLO'
        input(message: 'would you like to make a snapshot', id: 'snapshot', ok: 'yes', submitter: 'will', submitterParameter: 'yes')
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