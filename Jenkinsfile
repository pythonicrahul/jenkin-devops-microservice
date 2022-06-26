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
		stage('Build') {
			steps {
				sh "mvn --version"
				sh "docker version"
			}
		}

		stage('Test') {
			steps {
				echo "Test"
			}
		}

		stage('Integration Test') {
			steps {
				echo "Intergation Test"
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