pipeline {
   agent any 
   tools { 
        maven 'Maven-3.6.0' 
    
    }
 stages {
     stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '9e612bee-967f-4172-a07a-a36df0a85b62', url: 'https://github.com/GANKNIR/hello-world-war.git']]])
      }
    }
    stage('build') {
      steps {
        sh 'mvn clean install'
      }
    }
   stage('deploy') {
      steps {
     sh 'mv ${WORKSPACE}/target/hello-world-war-1.0.0.war ${WORKSPACE}/target/hello.war' 
      sh 'cp ${WORKSPACE}/target/hello.war /opt/tomcat/webapps/'
        }
  }
 }
} 