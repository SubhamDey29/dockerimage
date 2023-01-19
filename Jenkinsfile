pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhubaccount')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t abc/nodejsapp:2.0 .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push subham2920/sddey2920:2.0'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
