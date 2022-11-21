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
	environment {
		dockerHome = tool "myDocker"
		mavenHome = tool "myMaven"
		PATH="$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
			stage('Checkout') {
				steps {
					sh "mvn --version"
					sh "docker version"
					echo "Build"
					echo "Path - $PATH"
					echo "Build Number - $env.BUILD_NUMBER"
					echo "Build ID - $env.BUILD_ID"
					echo "Job Name - $env.JOB_NAME"
					echo "Build Tag - $env.BUILD_TAG"
					echo "Build URL - $env.BUILD_URL"
				}
			}
			stage ('Compile') {
				steps {
					sh "mvn clean compile"
				}
			}
			stage('Test') {
			steps {
				echo "mvn test"
				sh "mvn test"
			}
		}
			stage('Integration Test') {
			steps {
				echo "Integration Test"
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
			stage('Package') {
			steps {
				echo "Package Step"
				sh "mvn package -DskipTests"
			}
		}
			stage ('Build Docker Image') {
				steps {
					// docker build -t crepic21/currency-exchange-devops:$env.BUILD_TAG
					script {
						dockerImage = docker.build("crepic21/currency-exchange-devops:${env.BUILD_TAG}")
					}
				}
			}
			stage ('Push Docker Image') {
				steps {
					script {
						docker.withRegistry("", "dockerHub") {
							dockerImage.push();
							dockerImage.push('latest');
						}
					}
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