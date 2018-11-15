pipeline {

    agent {
                docker { image 'node:7-alpine' }
    };

    stages {



       def mvnHome

    stage('Test') {
                steps {
                    sh 'node --version'
                }
            }

       stage('Preparation') {
          git 'https://github.com/tvdgit/myservice'
          mvnHome = tool 'M3'
       }
       stage('Build') {

             sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"

       }
       stage('Results') {
          //junit '**/target/surefire-reports/TEST-*.xml'
          archive 'target/*.jar'
       }

       stage('Dockerize'){
            sh "echo hello"
       }
    }


}
