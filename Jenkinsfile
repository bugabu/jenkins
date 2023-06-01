pipeline {
	agent { docker { image  'node:13.8' } }
	stages {
		stage('Build') {
			steps {
				sh 'node --version'
				echo "Build"
				echo "BUILD NUMBER - $env.BUILD_NUMBER"
			}
		}
		stage('Test') {
			steps {
				echo "Test3"
			}
		}
	}
}
