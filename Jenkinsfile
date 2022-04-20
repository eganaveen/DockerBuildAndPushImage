pipeline{
	environment{
		imagename = "yenigul/hacicenkins"
		registryCredentials = 'dockerhub'
		dockerImage = ""
	}
	agent any
	stages{
		stage('Cloning git'){
			steps{
				git credentialsId: 'github', url: 'https://github.com/eganaveen/DockerBuildAndPushImage.git'
			}
		}
		stage('Building image'){
			steps{
				script{
					dockerImage = docker.build imagename
				}
			}
		}
		stage('Deploy Image'){
			steps{
				script{
					docker.withRegistry('',registryCredentials)
					dockerImage.push("$BUILD_NUMBER")
					 dockerImage.push('latest')
				}
			}
		}

	}
}
