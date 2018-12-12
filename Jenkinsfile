pipeline{
    agent any
    stages{
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
        parallel{
            stage('Test 1'){
                steps{
                    echo 'Inside test1 stage'
                }
            }
            stage('Test 2'){
                steps{
                    echo 'Inside test2 stage'
                }
            }
        }
        stage('Report'){
            steps{
                echo 'Inside Reporting stage'
            }
        }
    }
}




