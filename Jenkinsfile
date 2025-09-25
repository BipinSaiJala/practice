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

    stage('OWASP Dependency Check') {
      steps {
        dependencyCheck additionalArguments: '''
          --scan ./
          --out ./dependency-check-report
          --format ALL
          --prettyPrint
        ''', odcInstallation: 'OWASP-DepCheck-10'
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'dependency-check-report/**', allowEmptyArchive: true
    }
  }
}
