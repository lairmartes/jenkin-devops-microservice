pipeline {
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'

		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				sh "mvn --version"
				sh "docker version"
				echo "Build - Lair ===>"
				echo "$PATH"
				echo "Buiild Number: - $env.BUILD_NUMBER"
				echo "Job Name: $env.JOB_NAME"
				echo "<==== End of Build - Lair"
			}
		}

		stage ('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}

		stage('Test') {
			steps {
				sh "mvn test"
			}
		}

		stage('Integration Test') {
			steps {
				echo "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage('Build Docker Image') {
			steps {
				// docker build -t lairmartes/currency-exchange-devops:$env.BUILD_TAG
				script {
					docker.build("lairmartes/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		

		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', 'dockerhub') {
						dockerImage.push();
						dockerImage.push('latest')
					}
				}

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
