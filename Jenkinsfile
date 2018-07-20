node {
    def javaappImage
    def dbImage
    def dotnetapiImage
    
    stage('Clone repo') {
      checkout scm
    }
    stage('Build java-app') {
      javaappImage = docker.build("spara/java-app", "./java-app")
    } 
    stage('Build database') {
      dbImage = docker.build("spara/database", "./database")
    }
    stage('Build dotnet-api') {
      dotnetapiImage = docker.build("spara/dotnet-api", "./dotnet-api")
    }
    stage('Push java-app image') {
      docker.withRegistry("https://index.docker.io/v1/", "spara" ) {
        javaappImage.push("${env.BUILD_NUMBER}")
        javaappImage.push()
      }
    }
    stage('Push database image') {
      docker.withRegistry("https://index.docker.io/v1/", "spara" ) {
        dbImage.push("${env.BUILD_NUMBER}")
        dbImage.push()
      }
    }
    stage('Push dotnet-api image') {
      docker.withRegistry("https://index.docker.io/v1/", "spara" ) {
        dotnetapiImage.push("${env.BUILD_NUMBER}")
        dotnetapiImage.push()
      }
    }
}
