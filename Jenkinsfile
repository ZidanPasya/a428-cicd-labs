pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    // triggers {
    //     pollSCM('*/2 * * * *')
    // }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
        stage('Test') { 
            steps {
                sh './jenkins/scripts/test.sh'
                input message: 'Lanjutkan ke tahap Deploy?'
            }
        }
        stage('Deploy') { 
            steps {
                sh './jenkins/scripts/deploy.sh'
                sleep(60)
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}