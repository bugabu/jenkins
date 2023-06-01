pipeline {
	agent { docker { image  'node:13.8' } }
	environment {
		dockerHome = tool 'mydocker'
		dockerMaven = tool 'mymaven'
		PATH = "$dockerHome/bin:$dockerMaven/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				sh 'node --version'
				sh 'mvn --version'
				sh 'docker version' 
				echo "Build"
				echo "BUILD NUMBER - $env.BUILD_NUMBER"
				echo "BUILD ID - $env.BUILD_ID"
			}
		}
		stage('Compile') {
			steps {
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps {
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
	}
}

