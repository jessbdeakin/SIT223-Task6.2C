pipeline {
    agent any
    
    environment {
        DIRECTORY_PATH = "/c/test/"
        TESTING_ENVIRONMENT = "JessTest"
        PRODUCTION_ENVIRONMENT = "Jess"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch source code from directory path ${DIRECTORY_PATH}"
                echo 'Compile the code and generate artefacts'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Unit tests'
                echo 'Integration tests'
            }
        }
        
        stage('Code Quality Check'){
            steps {
                echo 'Check the quality of the code'
            }
        }
        
        stage('Deploy'){
            steps {
                echo "Deploy the app to testing environment ${TESTING_ENVIRONMENT}"
            }
        }
        
        stage('Approval'){
            steps {
                sleep(10)
            }
        }
        
        stage('Deploy to Production'){
            steps {
                echo "Deploy the app to production environment ${PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}
