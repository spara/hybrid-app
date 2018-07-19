node {
    checkout scm

    stage 'Build'
    def testImage = docker.build("spara/java-app", "./java-app") 
    
    stage 'Push Docker image'
    docker.withRegistry("https://index.docker.io/v1/", "spara" ) {
        testImage.push("${env.BUILD_NUMBER}")
        testImage.push()
    }

}
