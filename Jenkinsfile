node {
    stage('Clone repo') {
      checkout scm
    }
    stage('Build java-app') {
      def javaappImage = docker.build("spara/java-app", "./java-app")
    } 
    stage('Build database') {
      def dbImage = docker.build("spara/database", ./database")
    }
    stage('Build dotnet-api) {
      def dotnetapiImage = docker.build(spara/dotnet-api, "./dotnet-api")
    }
    stage('Push Docker image') {
      docker.withRegistry("https://index.docker.io/v1/", "spara" ) {
        java-appImage.push("${env.BUILD_NUMBER}")
        java-appImage.push()
        dbImage.push()
        dotnet-apiImage.push()
      }
    }
}
