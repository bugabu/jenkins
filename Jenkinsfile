pipeline {
	agent { docker { image  'node:13.8' } }
	environment {
		dockerHome = tool 'mydocker'
		dockerMaven = tool 'mymaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Build') {
			steps {
				sh 'node --version'
				echo "Build"
				echo "BUILD NUMBER - $env.BUILD_NUMBER"
				echo "BUILD ID - $env.BUILD_ID"
			}
		}
		stage('Test') {
			steps {
				echo "Test3"
			}
		}
	}
}
