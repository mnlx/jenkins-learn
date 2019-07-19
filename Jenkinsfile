pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                timeout(time: 10, unit: 'SECONDS') {
                    sh 'go run init.go'
                    sh '''
                        echo "This is working"
                        ls -lah
                    '''
                    retry(3) {
                        sh 'chmod +x flakey.sh'
                        sh './flakey.sh'
                    }
                }
            }
        }
    }
}