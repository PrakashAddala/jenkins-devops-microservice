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
		stage('Build'){
			steps{
				echo "PATH- $PATH"
				sh 'docker version'
				sh 'mvn --version'
				echo "Build Tag - $BUILD_TAG"
				echo "BUILD_URL- $BUILD_URL"
				echo "BUILD_NUMBER- $BUILD_NUMBER"			
			}
		}
		stage('Test'){
			steps{
				echo "Test"
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