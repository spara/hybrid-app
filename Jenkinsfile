node {
    checkout scm

    stage 'Build'
    def testImage = docker.build("java-app", "./java-app") 
    
    stage 'Push Docker image'
    withDockerRegistry("", "spara") {
        testImage.push()
    }

}
