pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode ture
                }
            }
            steps {
                sh '''
                    ls -al
                    node --version
                    npm --version
                                   '''
            }
        }
    }
}
