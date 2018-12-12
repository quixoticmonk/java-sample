pipeline{
    agent any
    stages{
        stage("Initialize"){
            steps{
                echo 'Inside the Initialize stage'
            }
         }
        stage("Checkout Code"){
            steps{
                echo 'Inside Code checkout stage'
            }
        }
        stage("Build Code"){
            steps{
                echo 'Inside Build Stage'
            }
        }
        stage("Test Stages"){
            parallel{
                stage('Unit Tests'){
                    steps{
                        echo 'Inside test1 stage'
                    }
                }
                stage('Integration Tests'){
                    steps{
                        echo 'Inside test2 stage'
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
                    steps(
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
        stage("Deploy to server"){
            steps{
                echo 'Deploy to Test Server'
            }
        }
        stage("Emails/Notifications"){
            steps{
                echo 'Inside Notifications stage'
            }
        }
    }
}




