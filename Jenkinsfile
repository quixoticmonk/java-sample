pipeline{
    agent any
    stages{
        stage("Checkout Code"){
            echo 'Inside Code checkout stage'
        }
        stage("Build Code"){
            echo 'Inside Build Stage'
        }
        parallel{
            stage('Test 1'){
                echo 'Inside test1 stage'
            }
            stage('Test 2'){
                echo 'Inside test2 stage'
            }
        }
        stage('Report'){
            echo 'Inside Reporting stage'
        }
    }
}




