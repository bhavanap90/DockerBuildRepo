pipeline {
  agent {
	dockerfile true
  }
  stages {
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t bhavanaprabhu/testrepo:FirstProject_v1 .'
      }
    }
    stage('Docker Push') {
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockercreds', passwordVariable: 'dockercredsPassword', usernameVariable: 'dockercredsUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push bhavanaprabhu/testrepo:FirstProject_v1'
        }
      }
    }
	stage('Docker Run') {
      agent any
      steps {
        sh 'docker run bhavanaprabhu/testrepo:FirstProject_v1'
      }
    }
  }
}