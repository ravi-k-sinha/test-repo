pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                
                sh chmod 777 ./flakey-deploy.sh
                
                retry(3) {
                    sh './flakey-deploy.sh'
                }
                
                sh chmod 777 ./health-check.sh

                timeout(time: 3, unit: 'MINUTES') {
                    sh './health-check.sh'
                }
            }
        }
    }
}
