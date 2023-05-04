pipeline {
	agent { docker { image 'maven:3.6.3' } }
	stages {
		stage('Build') {
			steps {
				sh "mvn --version"
				echo "Build"
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
