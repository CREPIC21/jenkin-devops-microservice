// SCRIPTED PIPELINE APROACH
// node {
// 	// stage('Build') {
// 	// 	echo "Build"
// 	// }
// 	// stage('Test') {
// 	// 	echo "Test"
// 	// }
// 	// stage('Integration Test') {
// 	// 	echo "Integration Test"
// 	// }
// 	echo "Build"
// 	echo "Test"
// 	echo "Integration Test"
// }

// DECLARETIVE PIPELINE APROACH
pipeline {
	// agent any
	// agent { docker {image "maven:3.6.3"}}
	agent { docker {image "node:alpine3.15"}}
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
				echo "Integration Test"
			}
		}
	} 
	post {
		always {
			echo "I am awsome. I run always."
		}
		success {
			echo "I run when you are successful"
		}
		failure {
			echo "I run when you fail"
		}
		changed {
			echo "I run when you build fails showing what changed and vice versa"
		}
	}
}