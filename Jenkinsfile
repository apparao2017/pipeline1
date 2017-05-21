pipeline {
  agent any
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/apparao2017/mvnrepo.git', branch: 'master')
      }
    }
    stage('Deploy') {
      steps {
        sh 'mvn clean compile package deploy'
      }
    }
  }
}