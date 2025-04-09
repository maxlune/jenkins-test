pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:20-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo 'Jenkins is installing project dependances'
                    ls -la
                    npm ci
                    echo 'Jenkins is creating the build'
                    npm run build
                    echo 'end'
                    ls -al
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:20-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                  echo "lancement des tests"
                  test -f dist/index.html
                '''
            }
        }
    }
}
