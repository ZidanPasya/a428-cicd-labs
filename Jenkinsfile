node {
    def dockerImage = 'node:16-buster-slim'
    triggers {
        pollSCM('*/2 * * * *') 
    }
    stage('Build') {
        echo 'Building the project...'
        try {
            docker.image(dockerImage).inside("-p 3000:3000") {
                sh 'npm install'
            }
        } catch (Exception e) {
            currentBuild.result = 'FAILURE'
            error "Build failed: ${e.message}"
        }
    }
    stage('Test') {
        echo 'Running tests...'
        try {
            docker.image(dockerImage).inside("-p 3000:3000") {
                sh './jenkins/scripts/test.sh'
            }
        } catch (Exception e) {
            currentBuild.result = 'FAILURE'
            error "Tests failed: ${e.message}"
        }
    }
}
// pipeline {
//     agent {
//         docker {
//             image 'node:16-buster-slim' 
//             args '-p 3000:3000' 
//         }
//     }
//     triggers {
//         pollSCM('*/2 * * * *')
//     }
//     stages {
//         stage('Build') { 
//             steps {
//                 sh 'npm install'
//             }
//         }
//         stage('Test') { 
//             steps {
//                 sh './jenkins/scripts/test.sh'
//             }
//         }
//     }
// }