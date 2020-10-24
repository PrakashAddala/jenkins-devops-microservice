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
	agent { docker{ image 'maven:3.6.3'}}
	stages{
		stage('Build'){
			steps{
				sh "mvn --version"
				echo 'Build'
			}
		}
		stage('Test'){
			steps{
				echo "Test"
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
}