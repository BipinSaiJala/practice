pipeline {
  agent { docker { image 'node:18-alpine' } }
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
