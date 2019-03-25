pipeline {
  agent none
  stages {
    stage('build') {
      agent any
      steps {
        echo 'run build'
      }
    }
    stage('Dev Deploy') {
      agent any
      steps {
        echo 'stop systems'
        echo 'deploy'
        echo 'Start Systems'
      }
    }
    stage('Create Snapshot?') {
      steps {
        emailext(body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS.<br/> <br/> Check console <a href="${BUILD_URL}/input">output</a> to view full results.<br/> If you cannot connect to the build server, check the attached logs.<br/> <br/> --<br/> Following is the last 100 lines of the log.<br/> <br/> --LOG-BEGIN--<br/> <pre style=\'line-height: 22px; display: block; color: #333; font-family: Monaco,Menlo,Consolas,"Courier New",monospace; padding: 10.5px; margin: 0 0 11px; font-size: 13px; word-break: break-all; word-wrap: break-word; white-space: pre-wrap; background-color: #f5f5f5; border: 1px solid #ccc; border: 1px solid rgba(0,0,0,.15); -webkit-border-radius: 4px; -moz-border-radius: 4px; border-radius: 4px;\'> ${BUILD_LOG, maxLines=100, escapeHtml=true} </pre> --LOG-END--', subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS.', from: 'admin@its.ny.gov', mimeType: 'text/html', replyTo: 'wilberncarey@hotmail.com', to: 'wilberncarey@hotmail.com')
        echo 'push snapshot to nexus'
      }
    }
    stage('Test Deploy') {
      steps {
        emailext(body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS.<br/> <br/> Check console <a href="${BUILD_URL}/input">output</a> to view full results.<br/> If you cannot connect to the build server, check the attached logs.<br/> <br/> --<br/> Following is the last 100 lines of the log.<br/> <br/> --LOG-BEGIN--<br/> <pre style=\'line-height: 22px; display: block; color: #333; font-family: Monaco,Menlo,Consolas,"Courier New",monospace; padding: 10.5px; margin: 0 0 11px; font-size: 13px; word-break: break-all; word-wrap: break-word; white-space: pre-wrap; background-color: #f5f5f5; border: 1px solid #ccc; border: 1px solid rgba(0,0,0,.15); -webkit-border-radius: 4px; -moz-border-radius: 4px; border-radius: 4px;\'> ${BUILD_LOG, maxLines=100, escapeHtml=true} </pre> --LOG-END--', subject: 'Deploy $BUILD_NUMBER to Test?', replyTo: 'wilberncarey@hotmil.com', to: 'wilberncarey@hotmil.com')
        echo 'Deploy to test'
      }
    }
    stage('QA Deploy') {
      steps {
        emailext(subject: 'Deploy $BUILD_NUMBER to QA', replyTo: 'wilberncarey@hotmil.com', to: 'wilberncarey@hotmil.com', body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS.<br/> <br/> Check console <a href="${BUILD_URL}/input">output</a> to view full results.<br/> If you cannot connect to the build server, check the attached logs.<br/> <br/> --<br/> Following is the last 100 lines of the log.<br/> <br/> --LOG-BEGIN--<br/> <pre style=\'line-height: 22px; display: block; color: #333; font-family: Monaco,Menlo,Consolas,"Courier New",monospace; padding: 10.5px; margin: 0 0 11px; font-size: 13px; word-break: break-all; word-wrap: break-word; white-space: pre-wrap; background-color: #f5f5f5; border: 1px solid #ccc; border: 1px solid rgba(0,0,0,.15); -webkit-border-radius: 4px; -moz-border-radius: 4px; border-radius: 4px;\'> ${BUILD_LOG, maxLines=100, escapeHtml=true} </pre> --LOG-END--', from: 'wilberncarey@hotmail.com')
        echo 'Run Deploy Scripts'
      }
    }
    stage('Create Version Release') {
      steps {
        emailext(subject: 'Would you like to create production release?', body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS.<br/> <br/> Check console <a href="${BUILD_URL}/input">output</a> to view full results.<br/> If you cannot connect to the build server, check the attached logs.<br/> <br/> --<br/> Following is the last 100 lines of the log.<br/> <br/> --LOG-BEGIN--<br/> <pre style=\'line-height: 22px; display: block; color: #333; font-family: Monaco,Menlo,Consolas,"Courier New",monospace; padding: 10.5px; margin: 0 0 11px; font-size: 13px; word-break: break-all; word-wrap: break-word; white-space: pre-wrap; background-color: #f5f5f5; border: 1px solid #ccc; border: 1px solid rgba(0,0,0,.15); -webkit-border-radius: 4px; -moz-border-radius: 4px; border-radius: 4px;\'> ${BUILD_LOG, maxLines=100, escapeHtml=true} </pre> --LOG-END--', from: 'wilberncarey@hotmil.com', replyTo: 'wilberncarey@hotmail.com', to: 'wilberncarey@hotmil.com')
        echo 'push to nexus'
      }
    }
    stage('Prod Deploy') {
      steps {
        emailext(subject: 'Release team - Deploy to Prod?', body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS.<br/> <br/> Check console <a href="${BUILD_URL}/input">output</a> to view full results.<br/> If you cannot connect to the build server, check the attached logs.<br/> <br/> --<br/> Following is the last 100 lines of the log.<br/> <br/> --LOG-BEGIN--<br/> <pre style=\'line-height: 22px; display: block; color: #333; font-family: Monaco,Menlo,Consolas,"Courier New",monospace; padding: 10.5px; margin: 0 0 11px; font-size: 13px; word-break: break-all; word-wrap: break-word; white-space: pre-wrap; background-color: #f5f5f5; border: 1px solid #ccc; border: 1px solid rgba(0,0,0,.15); -webkit-border-radius: 4px; -moz-border-radius: 4px; border-radius: 4px;\'> ${BUILD_LOG, maxLines=100, escapeHtml=true} </pre> --LOG-END--')
        input(message: 'Deploy?', id: 'relprodapprove', ok: 'YES', submitter: 'will')
        emailext(body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS.<br/> <br/> Check console <a href="${BUILD_URL}/input">output</a> to view full results.<br/> If you cannot connect to the build server, check the attached logs.<br/> <br/> --<br/> Following is the last 100 lines of the log.<br/> <br/> --LOG-BEGIN--<br/> <pre style=\'line-height: 22px; display: block; color: #333; font-family: Monaco,Menlo,Consolas,"Courier New",monospace; padding: 10.5px; margin: 0 0 11px; font-size: 13px; word-break: break-all; word-wrap: break-word; white-space: pre-wrap; background-color: #f5f5f5; border: 1px solid #ccc; border: 1px solid rgba(0,0,0,.15); -webkit-border-radius: 4px; -moz-border-radius: 4px; border-radius: 4px;\'> ${BUILD_LOG, maxLines=100, escapeHtml=true} </pre> --LOG-END--', subject: 'Operations - Deploy to Prod')
        input(message: 'Operations Prod Approvel', id: 'opsprodapprovel', ok: 'YES', submitter: 'will')
        echo 'deploy script'
      }
    }
  }
}