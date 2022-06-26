// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Test"
// }

pipeline {
	agent {
		docker {
			image "maven:3.6.3"
		}
	}
	stages {
		stage('Build') {
			steps {
				sh "mvn --version"
				echo "Build"
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