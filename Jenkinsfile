pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'mvn clean install', returnStatus: true)
      }
    }
    stage('') {
      steps {
        git(url: 'https://github.com/quixoticmonk/java-sample.git', branch: 'master', poll: true)
      }
    }
  }
}