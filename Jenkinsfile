pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				echo "Build - Lair"
			}
		}
		stage('Test') {
			steps {
				echo "Test - Lair"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test - Lair"
			}
		}
	}
	
	post {
		always {
			echo 'I will alwyas be here... and will always run'
		}
		success {
			echo 'I run ONLY when everything went well'
		}
		failure {
			echo 'I run ONLY when something whent WRONG'
		}
	}
}
