pipeline {
	agent any
	environment {
		dockerHome = tool 'mydocker'
		mavenHome = tool 'mymaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version' 
				echo "Build"
				echo "BUILD TAG - $env.BUILD_TAG"
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
		
		stage('Build Docker Image') {
			steps {
				//"docker build -t bugabu/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("bugabu/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		
		stage('Push Docker Image') {
			steps {
				script {
					dockerImage.push();
					dockerImage.push('latest');
				}
			}
		}
	}
}

