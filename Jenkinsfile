node {
    docker.image('node:16-buster-slim').withRun('-p 3000:3000') {
        // Stage: Build
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        // Stage: Test
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
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