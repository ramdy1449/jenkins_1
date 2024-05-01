pipeline {
  agent any
  tools {
    maven 'Maven'
  }
  stages{
    stage('1-cloning project repo'){
      steps{
       checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/ramdy1449/jenkins_1.git']])
      }
    }
    stage('2-cleanws'){
      steps{
        sh 'mvn clean'
      }
    }
    stage('3-mavenbuild'){
      steps{
        sh 'mvn package'
      }
    }
     stage('codequality'){
        steps{
       sh "mvn clean verify sonar:sonar \
        -Dsonar.projectKey=new \
        -Dsonar.host.url=http://3.16.160.73:9000 \
        -Dsonar.host=sqp_016271a16f0658ed81dfa440b6f5ee99114beb46"
      }
    }
  }
}
