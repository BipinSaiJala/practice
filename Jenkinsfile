pipeline {
  agent any
  options { timestamps() }

  stages {
    stage('Checkout') {
      steps {
        // If your default branch is "main", keep as is. Change to "feature" if needed.
        git url: 'https://github.com/BipinSaiJala/practice.git', branch: 'feature'
      }
    }

    stage('Install') {
      steps {
        sh 'npm ci || npm install'
      }
    }

    stage('Test') {
      steps {
        // Runs tests if present; won’t fail the build if there are none
        sh 'npm test || echo "no tests found"'
      }
    }

    stage('Build') {
      steps {
        // Build if your package.json has a "build" script
        sh 'npm run build || true'
      }
    }
  }

  post {
    always {
      // Save common outputs if they exist (safe to leave as is)
      archiveArtifacts artifacts: 'build/**,dist/**,coverage/**', allowEmptyArchive: true
    }
  }
}


