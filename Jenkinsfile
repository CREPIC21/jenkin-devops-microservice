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
	stages {
		stage('Build') {
			steps {
				echo "Build"
				echo "Test"
				echo "Integration Test"
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
}