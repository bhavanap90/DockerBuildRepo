pipeline {
  agent {
	dockerfile true
  }
  stages {
    stage('Docker Build') {
      agent any
      steps {
        sh 'sudo docker build -t bhavanaprabhu/testrepo:FirstProject_v1 .'
      }
    }
    stage('Docker Push') {
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockercreds', passwordVariable: 'dockercredsPassword', usernameVariable: 'dockercredsUser')]) {
          sh 'sudo docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}'
          sh 'sudodocker push bhavanaprabhu/testrepo:FirstProject_v1'
        }
      }
    }
	stage('Docker Run') {
      agent any
      steps {
        sh 'sudo docker run bhavanaprabhu/testrepo:FirstProject_v1'
      }
    }
  }
}