pipeline {
  agent any
  options { timestamps() }

  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/BipinSaiJala/practice.git', branch: 'feature'
        stash name: 'src', includes: '**/*'
      }
    }

    stage('Parallel') {
      parallel {
        stage('Install') {
          steps {
            deleteDir()
            unstash 'src'
            sh 'npm ci || npm install'
          }
        }
        stage('OWASP Dependency Check') {
          steps {
            deleteDir()
            unstash 'src'
            dependencyCheck additionalArguments: '''
              --scan ./
              --out ./dependency-check-report
              --format ALL
              --prettyPrint
            ''', odcInstallation: 'OWASP-DepCheck-10'

            dependencyCheckPublisher(
              pattern: 'dependency-check-report/dependency-check-report.xml',
              failedTotalCritical: 1,
              unstableTotalHigh: 1
            )
          }
        }
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'dependency-check-report/**', allowEmptyArchive: true
    }
  }
}
