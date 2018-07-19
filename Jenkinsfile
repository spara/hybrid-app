node {
    checkout scm

    stage 'Build'
    def testImage = docker.build("java-app", "./java-app") 
    
    stage 'Push Docker image'
    withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: params.JP_DockerMechIdCredential, usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) {
			usr = USERNAME
			pswd = PASSWORD
     }

    withDockerRegistry([ url: "https://index.docker.io/v1/", credentialsId: "spara" ]) {
        sh "docker login -u ${usr} -p ${pswd}"
        testImage.push("${env.BUILD_NUMBER}")
        testImage.push()
    }

}
