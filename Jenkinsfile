node {
    withDockerContainer(image: 'node:16-buster-slim', args: '-p 3000:3000'){
        // triggers{
        //     pollSCM('*/2 * * * *')
        // }
        stage('Build'){
            sh 'npm install'
        }
    }
}