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
            app.push("FirstProject"+"${env.BUILD_NUMBER}")
        }
    }
	stage('Run container') {
        docker.image('bhavanaprabhu/testrepo:FirstProject'+'${env.BUILD_NUMBER}').withRun() {c-> sh "docker logs ${c.id}"}
	}
}
