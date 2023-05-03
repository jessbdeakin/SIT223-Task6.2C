pipeline {
	agent any
	
	environment {
		DIRECTORY_PATH = "/c/home/university/223-PRO/6.2C/"
		TESTING_ENVIRONMENT = "JessTest"
		PRODUCTION_ENVIRONMENT = "Jess"
	}

	stages {
		stage('Build') {
			steps {
				echo "Fetch source code from directory path ${DIRECTORY_PATH}"
				echo 'Compile the code and generate artefacts'

				git url: 'https://github.com/jessbdeakin/SIT223-Task6.2C.git'

			}
		}
		
		stage('Unit and Integration Tests') {
			steps {
				echo 'Unit tests'
				echo 'Integration tests'
			}
		}
		
		stage('Code Analysis'){
			steps {
				echo 'Check the quality of the code'
			}
		}
		  
		stage('Securityy Scan'){
			steps {
				echo 'Meow.'
			}
		}
		
		stage('Deploy to Staging'){
			steps {
				echo "Deploy the app to testing environment ${TESTING_ENVIRONMENT}"
			}
		}
		
		stage('Integration Tests on Staging'){
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
