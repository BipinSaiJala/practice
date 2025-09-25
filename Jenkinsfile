
pipeline {
  agent any
  tools {
    nodejs 'NodeJS 24.8.0'   // <-- exactly the tool name you configured
  }
  stages {
    stage('Node Version') {
      steps {
        sh '''
          node -v
          npm -v
        '''
      }
    }
  }
}
