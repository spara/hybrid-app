node {
    checkout scm

    stage 'Build'
    def testImage = docker.build("java-app", "./java-app") 
    
    stage 'Push Docker image'
    withDockerRegistry([ url: "https://index.docker.io/v1/", credentialsId: "spara" ]) {
        testImage.push("${env.BUILD_NUMBER}")
        testImage.push()
    }

}
