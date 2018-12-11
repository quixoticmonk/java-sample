pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/quixoticmonk/java-sample.git', branch: 'master', poll: true)
      }
    }
    
    stage('Build') {
      steps {
        bat(script: 'mvn clean install', returnStatus: true)
      }
    }
    
  }
}
