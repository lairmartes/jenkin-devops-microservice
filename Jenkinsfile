pipeline {
	agent any
	// agent { docker { image 'maven:3.6.3' } }
	stages {
		stage('Build') {
			steps {
				//sh "mvn --version"
				echo "Build - Lair ===>"
				echo "$PATH"
				echo "Buiild Number: - $env.BUILD_NUMBER"
				echo "Job Name: $env.JOB_NAME"
				echo "<==== End of Build - Lair"
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
