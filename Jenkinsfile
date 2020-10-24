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

	environment {
		dockerHome= withtool 'myDocker'
		mavenHome= tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	agent any

	stages{
		stage('Build'){
			steps{
				sh 'docker version'
				sh 'mvn --version'
				echo "Build Tag - $BUILD_TAG"
				echo "BUILD_URL- $BUILD_URL"
				echo "BUILD_NUMBER- $BUILD_NUMBER"
				echo "PATH- $PATH"
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