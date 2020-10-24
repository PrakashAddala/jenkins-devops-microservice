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
	agent any
	//agent {docker{ image 'maven:3.6.3'}}
	stages{
		stage('Build'){
			steps{
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