pipeline {
  agent any
  tools {
    nodejs 'NodeJS 24.8.0'   // <-- replace with the EXACT tool name you set
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
    stage('Install deps') {
      steps {
        sh '''
          if [ -f package-lock.json ]; then
            npm ci
          else
            npm install
          fi
        '''
      }
    }
  }
}
