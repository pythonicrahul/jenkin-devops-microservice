// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Test"
// }

pipeline {
	agent any
	// agent {
	// 	docker {
	// 		image "maven:3.6.3"
	// 	}
	// }

	environment {
		dockerHome = tool('myDocker')
		mavenHome = tool('myMaven')
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				sh "mvn --version"
				sh "docker version"
			}
		}

		stage('Compile') {
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
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage('Build Docker Image'){
			steps {
				// docker build  -t rjsoft3186/currency-exchange-devops:$env.BUILD_TAG
				script {
					dockerImage = docker.build("rjsoft3186/currency-exchange-devops:${env.BUILD_TAG}");
				}
			}
		}

		stage('Push Docker Image'){
			steps {
				script {
					docker.withRegistry('', 'dockerhub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}
		}
	} 

	post {
		always {
			echo 'I am awesomse. I run always'
		}
		success {
			echo 'I run when its success'
		}
		failure {
			echo 'I run when its failure'
		}
	}

}