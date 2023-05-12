pipeline {
	agent any
	
	environment {
		GIT_REPOSITORY = "https://github.com/jessbdeakin/SIT223-Task6.2C.git"
		GIT_BRANCH = "main"

		EMAIL_ADDRESS = "s222317449@deakin.edu.au"

		BUILD_PATH = 'build'

		BUILD_TEST_PATH = 'btest'
		STAGING_TEST_PATH = 'stest'

		CPPCHECK_LOG = 'cppcheck.log'

		PRODUCTION_ENVIRONMENT = 'jessprod'
		TESTING_ENVIRONMENT = 'jesstest'
	}

	stages {
		stage('Build') {
			steps {

				echo "Fetch source code"
				git branch: "${GIT_BRANCH}", url: "${GIT_REPOSITORY}"

				echo 'Build code with Gradle'
				// bat 'gradle clean build'
			}
		}
		
		stage('Unit and Integration Tests') {
			steps {
				echo 'Run unit tests generated with the Google Test framework'
				// bat '%BUILD_TEST_PATH%/test.exe'

				mail to: "${EMAIL_ADDRESS}", subject: "[JENKINS] Successful test", body: "${currentBuild.rawBuild.log}"
			}
			post {
				failure {
					mail to: "${EMAIL_ADDRESS}", subject: "[JENKINS] Failed test", body: "${currentBuild.rawBuild.log}"
				}
			}
		}
		
		stage('Code Analysis'){
			steps {
				echo 'Perform code analysis with Cppcheck'
				// bat 'cppcheck --enable=all %BUILD_PATH% 2> %CPPCHECK_LOG%'
			}
		}
		  
		stage('Security Scan'){
			steps {
				echo 'Security scan.'

				mail to: "${EMAIL_ADDRESS}", subject: "[JENKINS] Successful security scan", body: "${currentBuild.rawBuild.log}"
			}
			post {
				failure {
					mail to: "${EMAIL_ADDRESS}", subject: "[JENKINS] Failed security scan", body: "${currentBuild.rawBuild.log}"
				}
			}
		}
		
		stage('Deploy to Staging'){
			steps {
				echo "Deploy the app to testing environment ${TESTING_ENVIRONMENT}"
			}
		}
		
		stage('Integration Tests on Staging'){
			steps {
				echo 'Run integration tests generated with the Google Test framework'
				// bat '%STAGING_TEST_PATH%/test.exe'
			}
		}
		
		stage('Deploy to Production'){
			steps {
				echo "Deploy the app to production environment ${PRODUCTION_ENVIRONMENT}"
			}
		}
	}
}
