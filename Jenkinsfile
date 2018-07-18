node {
    checkout scm
    def testImage = docker.build("java-app", "./java-app") 
    customImage.push()

}
