// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Test"
// }

pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
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