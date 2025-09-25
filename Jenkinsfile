pipeline{
    agent any

    tools{
        nodejs 'NodeJS 24.8.0'
    }

    stages{
        stage('Node Version'){
            steps{
                sh '''
                    node -v
                    npm -v

                '''
            }
        }
    }
}