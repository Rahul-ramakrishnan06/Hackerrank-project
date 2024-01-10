pipeline {
	agent{
        label 'kmaster'
	}

    environment {
        DOCKER_IMAGE = 'nodejs-multi_version-10_web:2'
    }
	stages{
		stage('Build'){
			steps{
				script{
                    sh 'docker-compose build web'
				}
			}
		}

		stage('sed command'){
			steps{
				script{
                    sh 'sed -i "s|image:.*|image: ${DOCKER_IMAGE}|" nodejs.yaml'
				}
			}
		}

		stage('sed command'){
			steps{
				script{
                    sh 'kubectl apply -f nodejs.yaml'
				}
			}
		}
	}
}
