node {
    stage('Clone repo') {
      checkout scm
    }
    stage('Build java-app') {
      def javaappImage = docker.build("spara/java-app", "./java-app")
    } 
    stage('Build database') {
      def dbImage = docker.build("spara/database", "./database")
    }
    stage('Build dotnet-api') {
      def dotnetapiImage = docker.build("spara/dotnet-api", "./dotnet-api")
    }
    stage('Push java-app image') {
      docker.withRegistry("https://index.docker.io/v1/", "spara" ) {
        // java-appImage.push("${env.BUILD_NUMBER}")
        java-appImage.push()
      }
    }
    // stage('Push database image') {
    //   docker.withRegistry("https://index.docker.io/v1/", "spara" ) {
    //     dbImage.push("${env.BUILD_NUMBER}")
    //     dbImage.push()
    //   }
    // }
    // stage('Push dotnet-api image') {
    //   docker.withRegistry("https://index.docker.io/v1/", "spara" ) {
    //     // dotnetapiImage.push("${env.BUILD_NUMBER}")
    //     dotnetapiImage.push()
    //   }
    // }
}
