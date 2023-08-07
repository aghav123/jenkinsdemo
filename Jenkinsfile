pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'this is build stage'
        sh 'mvn clean '
        sh 'mvn compile'
        sh 'mvn test'
        sh 'mvn install'
      }
    }

    stage('test') {
      steps {
        echo 'install tomcat'
        sh '''sudo apt install default-jdk
sudo yum install java-1.8.0-openjdk
# Replace the URL with the download link for the desired Tomcat version
wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.52/bin/apache-tomcat-9.0.52.tar.gz
tar xzf apache-tomcat-9.0.52.tar.gz -C /opt
sudo ln -s /opt/apache-tomcat-9.0.52 /opt/tomcat
export CATALINA_HOME=/opt/tomcat
export PATH=$CATALINA_HOME/bin:$PATH
/opt/tomcat/bin/startup.sh
'''
      }
    }

    stage('deploy') {
      steps {
        echo 'this is deploy stage'
      }
    }

  }
}