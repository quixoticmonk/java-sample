pipeline{
    agent any

    stages{
        stage("Initialize"){
            steps{
                echo 'Inside the Initialize stage'
                echo ' '
            }
         }
        stage("Build Code"){
            steps{
                echo 'Inside Build Stage'
                sh 'mvn --version'
            }
        }
        stage("Dependency check"){
            steps{
                dependencyCheck additionalArguments: '', odcInstallation: 'OwaspDep'
                dependencyCheckPublisher pattern: ''
            }
        }
        stage("Test Stages"){
            parallel{
                stage('Unit Tests'){
                    steps{
                        echo 'Inside unit tests stage'
                        sh 'mvn clean package'
                    }
                }
                stage('Integration Tests'){
                    steps{
                        echo 'Inside Integration tests stage'
                    }
                }
                stage('Functional UI Tests'){
                    steps{
                        echo 'Inside UI tests'
                    }
                }
            }
        }
        stage("Code Scan"){
            parallel{
                stage('Static Scan'){
                    steps{
                        echo 'Inside Static Scan'
                    }
                }
                stage('SonarQube'){
                    steps{
                        echo 'Inside SonarQube stage'
                    }
                }
                stage('BlackDuck scans'){
                    steps{
                        echo 'Inside blackduck scans'
                    }
                }
            }
        }
        stage("Upload to Artefactory"){
            steps{
                echo 'Inside Artefactory stage'
            }
        }
        stage("Pre-Deploy Tasks"){
            steps{
                echo 'Predeploy tasks'
            }
        }
        stage('Should we deploy to Dev ?') {
          agent none
          steps {
            script {
              env.USER_INPUT = input message: 'User input required',
                  parameters: [choice(name: 'Should we deploy to Dev?', choices: 'no\nyes', description: 'Choose "yes" if you want to deploy this build')]
            }
          }
        }
        stage("Deploy to server"){
            when{
                environment name: 'USER_INPUT', value: 'yes'
            }
            steps{
                echo 'Deploy to Test Server'
                pushToCloudFoundry cloudSpace: 'manu',
                credentialsId: '37641d8f-73e2-4534-9e60-71f6aadd9e51',
                organization: 'Columbus-Dev', target: 'https://api.sys.apbg.apcf.io'
            }
        }
        stage('performance Tests'){
            steps{
                echo 'Inside perf tests'
            }
        }
        stage("Emails/Notifications"){
            steps{
                echo 'Inside Notifications stage'
            }
        }
    }
     post{
        always{
            archive "target/**/*"
            junit 'target/surefire-reports/*.xml'
        }
    }
}




