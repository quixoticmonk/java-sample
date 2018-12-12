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


    }

    parallel{

        stage('Test1') {
          steps {
            echo ' test1'
                }
        }

         stage('Test2') {
                  steps {
                    echo ' test1'
                        }
                }
    }

    post {
        success {
        junit 'target/surefire-reports/**/*.xml'
                }
      }


  }

}