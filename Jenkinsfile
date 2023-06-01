pipeline {
	agent any
	environment {
		dockerHome = tool 'mydocker'
		mavenHome = tool 'mymaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
// 		stage('Checkout') {
// 			steps {
// 				sh 'mvn --version'
// 				sh 'docker version' 
// 				echo "Build"
// 				echo "BUILD TAG - $env.BUILD_TAG"
// 				echo "BUILD NUMBER - $env.BUILD_NUMBER"
// 				echo "BUILD ID - $env.BUILD_ID"
// 			}
// 		}
		
// 		stage('Compile') {
// 			steps {
// 				sh 'mvn clean compile'
// 			}
// 		}
		
// 		stage('Test') {
// 			steps {
// 				sh 'mvn test'
// 			}
// 		}
		
// 		stage('Package') {
// 			steps {
// 				sh 'mvn package -DskipTests'
// 			}
// 		}
		
// 		stage('Build Docker Image') {
// 			steps {
// 				//"docker build -t bugabu/currency-exchange-devops:$env.BUILD_TAG"
// 				script {
// 					dockerImage = docker.build("bugabu/currency-exchange-devops:${env.BUILD_TAG}")
// 				}
// 			}
// 		}
		
		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', '687513b5-932d-464e-82d8-3d80db2ec231') {
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}
		}
	}
}

