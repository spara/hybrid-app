node {
    checkout scm

    stage 'Build'
    def testImage = docker.build("java-app", "./java-app") 
    
    stage 'Push Docker image'
    docker.withRegistry("https://registry.hub.docker.com", "spara") {
        testImage.push()
    }

}
