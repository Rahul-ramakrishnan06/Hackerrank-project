pipeline {
    agent{
        label 'nodejs'
	}

    environment {
        // Set your Docker Hub credentials
        DOCKER_HUB_USERNAME = credentials('rahulkarthi54321	')
        DOCKER_HUB_PASSWORD = credentials('rahul@123')
        
        // Set your Docker image details
        DOCKER_IMAGE_NAME = 'rahulkarthi54321/nodejsdockerimage'
        DOCKER_IMAGE_TAG = 'latest'
    }

    stages {

		stage('Build'){
			steps{
				script{
                    sh 'docker-compose build web'
				}
			}
		}

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        docker.image("${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}").push()
                    }
                }
            }
        }
    }
}

