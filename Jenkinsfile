node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("bhavanaprabhu/testrepo:FirstProject")
    }


    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockercreds') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}