node {
    checkout scm

    stage 'Build'
    def java-appImage = docker.build("spara/java-app", "./java-app") 
    def dbImage = docker.build("spara/database", ./database")
    def dotnet-apiImage = docker.build(spara/dotnet-api, "./dotnet-api")
    
    stage 'Push Docker image'
    docker.withRegistry("https://index.docker.io/v1/", "spara" ) {
        java-appImage.push("${env.BUILD_NUMBER}")
        java-appImage.push()
        dbImage.push()
        dotnet-apiImage.push()
    }

}
