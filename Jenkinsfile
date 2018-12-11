pipeline {
  agent any
  tools {
  maven 'Maven3'
  jdk 'JDK1.8'
  }
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/quixoticmonk/java-sample.git', poll: true)
      }
    }
    stage('Build') {
      steps {
        bat(script: 'mvn clean install', returnStatus: true)
      }
      post {
        success {

        junit 'target/surefire-reports/**/*.xml'
        }

      }

    }
  }
}