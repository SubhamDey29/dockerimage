pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhubaccount')
    EC2_CREDENTIALS = credentials('43.205.243.213')
  }
  stages {
    /*stage('Build') {
      steps {
        sh 'docker build -t subham2920/sddey2920:2.0 .'
      }
    }*/
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    /*stage('Push') {
      steps {
        sh 'docker push subham2920/sddey2920:2.0'
      }
    }*/
    stage('EC2'){
      steps{
       sh 'echo "private key at $EC2_CREDENTIALS"'
       sh 'echo "user at $EC2_CREDENTIALS_USR"'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
