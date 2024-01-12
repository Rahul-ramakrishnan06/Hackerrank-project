pipeline {
	agent{
        label 'nodejs'
	}

	tools {
        nodejs 'Node.js'
    }

    environment {
        DOCKER_IMAGE = 'nodejs-multi_version-10_web:latest'
		SONARQUBE_HOME = tool 'SonarQubeScanner'
    }
	stages{
		stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

		stage('Build'){
			steps{
				script{
                    sh 'node app.js'
				}
			}
		}
	}
}
