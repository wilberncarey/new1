pipeline {
  agent none
  stages {
    stage('build') {
      agent any
      steps {
        echo 'run build'
      }
    }
    stage('Prod Deploy') {
      agent any
      steps {
        input(message: 'Operations Prod Approvel', id: 'app1', ok: 'YES', submitter: 'will', submitterParameter: '$PROJECT_NAME1234')
        echo '${PROJECT_NAME1234}'
        sh 'echo "$PROJECT_NAME1234"'
      }
    }
  }
}