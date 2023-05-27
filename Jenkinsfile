pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    DOCKERHUB_LOCATION = 'eduard1001171985'
    VERSION = 'v1.0.0'
  }
  stages {
    stage('Build') {
      steps {
        sh 'podman build --platform linux/arm64/v8 -t eduard1001171985/hello-world:$VERSION -t eduard1001171985/hello-world:latest -f hello-world-nginx/Dockerfile'
        sh 'podman build --platform linux/amd64 -t eduard1001171985/hello-world:$VERSION -t eduard1001171985/hello-world:latest -f hello-world-nginx/Dockerfile'
        sh 'podman build --platform linux/arm64/v8 -t eduard1001171985/hello-world-secure:$VERSION -t eduard1001171985/hello-world-secure:latest -f hello-world-nginx/secure/Dockerfile'
        sh 'podman build --platform linux/amd64 -t eduard1001171985/hello-world-secure:$VERSION -t eduard1001171985/hello-world-secure:latest -f hello-world-nginx/secure/Dockerfile'
      }
    }
    //stage('Login') {
    //  steps {
    //    sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
    //  }
    //}
    //stage('Push') {
    //  steps {
    //    sh 'docker push lloydmatereke/jenkins-docker-hub'
    //  }
    //}
  }
  //post {
  //  always {
  //    sh 'docker logout'
  //  }
  //}
}