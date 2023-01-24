pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhubaccount')
    
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
    stage('Ansible'){
      steps{
          ansiblePlaybook credentialsId: '43.205.243.213', disableHostKeyChecking: true, installation: 'ansible', inventory: 'test.inv', playbook: 'docker-ansible.yml'
       
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
