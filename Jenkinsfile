pipeline {
	agent any
	
	environment {
		SOURCE_PATH = ".\\app\\src\\"
		TESTING_ENVIRONMENT = "JessTest"
		PRODUCTION_ENVIRONMENT = "Jess"
	}

	stages {
		stage('Build') {
			steps {
				echo "Fetch source code"
				echo 'Compile the code and generate artefacts'

				git branch: 'main', url: 'https://github.com/jessbdeakin/SIT223-Task6.2C.git'

				bat 'gradle clean build'
			}
		}
		
		stage('Unit and Integration Tests') {
			steps {
				echo 'Unit tests'
				echo 'Integration tests'

				bat '.\\app\\build\\exe\\main\\debug\\appTest.exe'
				// 
			}
		}
		
		stage('Code Analysis'){
			steps {
				echo 'Check the quality of the code'

				bat 'cppcheck %SOURCE_PATH% 2> cppcheck.xml'
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
