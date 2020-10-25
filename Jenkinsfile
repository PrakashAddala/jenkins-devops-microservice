// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('IntegrationTest') {
// 		echo "Test"
// 	}
// }

//declarative

pipeline{
	//agent any
	//agent {docker{ image 'maven:3.6.3'}}
	agent any
	// tools {
  	// 	maven 'myMaven'
	// 	dockerTool 'myDocker'
	// }

	environment{
		dockerHome= tool 'myDocker'
		mavenHome= tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
				echo "PATH- $PATH"
				sh 'docker version'
				sh 'mvn --version'
				echo "Build Tag - $BUILD_TAG"
				echo "BUILD_URL- $BUILD_URL"
				echo "BUILD_NUMBER- $BUILD_NUMBER"			
			}
		}
		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				sh "mvn test"
			}
		}		
		
		stage('Integration Test'){
			steps{
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage('Package'){
			steps{
				sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image'){
			steps{
				// "docker build -t prakash46/docker-repo:$env.BUILD_TAG"
				script{
					dockerImage=docker.build("prakash46/docker-repo:${env.BUILD_TAG}")
				}
			}
		}

		stage('Push Docker Image'){
			steps{
				docker.withRegistry('','dockerhub'){
				dockerImage.push();
				dockerImage.push('latest');
				}
			}
		}
	}
	post{
			always{
				echo "Iam awesome always"
			}
			success{
				echo "Iam successful"
			}
			failure{
				echo "Something has failed"
			}
		}
}

//added script file
