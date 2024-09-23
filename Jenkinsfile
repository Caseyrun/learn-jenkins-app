pipeline {
    agent any

    stages {
        // This is a comment
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -al
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -al
                     '''
            } 
        }
         stage('test') {
            // This is test stage
            /* this is a lot
                2
                3
                4
            */
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                   # test -f build/index.html
                    npm test
                    
                     '''
            } 
        }
      stage('E2E') {
            // This is test stage
            /* this is a lot
                2
                3
                4
            */
            agent{
                docker{
                    image 'mcr.microsoft.com/playwright:v1.47.2-noble'
                    reuseNode true
                 
                }
            }
            steps {
                sh '''
                   npm install serve
                   learn-jenkins-app/node_modules/.bin/serve -s build
                   npx playwright
                     '''
            } 
        }    
    }

    post{
        always{
            junit 'test-results/junit.xml'
        }
    }
}
