pipeline {
    agent any

    stages {
        stage('Git-Checkout') {
            steps {
                echo 'Checking out from Git Repo'
                git branch: 'main', credentialsId: '422ac9a6-0960-47e6-bd65-729956940d73', url: 'https://github.com/grjangir/pipeline_script.git'
            }
        }
    
        stage('Build'){
            steps {
                echo 'Building the checked-out project!'
                bat 'Build.bat'
            }
        }   
    
        stage('Unit-Test'){
            steps {
                echo 'Running Junit Tests'
                bat 'Unit.bat'
            }
        }   
    
        stage('Quality-Gate'){
            steps {
                echo 'Verifying Quality Gates'
                bat 'Quality.bat'
            }
        }
    
        stage('Deploy'){
            steps {
                echo 'Deploying to Stage Environments for more tests!'
                bat 'Deploy.bat'
            }
        }
    
    }

    post{
        always{
            echo 'this will always run'
        }
        success{
            echo 'This will run only if successful'
        }
        failure{
            echo 'This will run only if failed'
        }
        unstable{
            echo 'This will only run if build was marked as unstable'
        }
        changed{
            echo 'This will run only if the state of the pipeline has changed'
            echo 'For example, if the pipeline was previously failing but is now successful'
        }
    }
}
