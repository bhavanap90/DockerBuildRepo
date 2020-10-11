node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("FirstProject")
    }


    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockercreds') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}