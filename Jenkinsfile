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
        sh '''temp=$(cat /var/lib/jenkins/jobs/apparao2017/jobs/pipeline1/branches/master/builds/lastStableBuild/log | grep war| grep Uploading| sed -e "s/Uploading: / /")
echo "APPARAO"
echo $temp
cd /opt/
sudo wget $temp -O javaee7.war
sudo tomcat/bin/shutdown.sh
rm -rf tomcat/webapps/*
mv javaee7.war tomcat/webapps/
sudo tomcat/bin/startup.sh 
'''
      }
    }
  }
}