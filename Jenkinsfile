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
    stage('deploy tomcat') {
      steps {
        sh '''echo cat /var/lib/jenkins/jobs/apparao2017/jobs/pipeline1/branches/master/builds/lastStableBuild/log | grep war| grep Uploading| sed -e "s/Uploading: / /"
#echo $URL
#cd /opt/
#sudo wget $URL -O javaee7.war
'''
      }
    }
  }
}