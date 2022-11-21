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
	agent any
	// agent { docker {image "maven:3.6.3"}}
	// agent { docker {image "node:alpine3.15"}}
	stages {
			stage('Build') {
				steps {
					// sh "node --version"
					echo "Build"
					echo "Path - $PATH"
					echo "Build Number - $env.BUILD_NUMBER"
					echo "Build ID - $env.BUILD_ID"
					echo "Job Name - $env.JOB_NAME"
					echo "Build Tag - $env.BUILD_TAG"
					echo "Build URL - $env.BUILD_URL"
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