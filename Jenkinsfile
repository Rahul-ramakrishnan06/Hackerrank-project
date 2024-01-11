pipeline {
	agent{
        label 'nodejs'
	}

    environment {
        DOCKER_IMAGE = 'nodejs-multi_version-10_web:latest'
    }
	stages{
		stage('Build'){
			steps{
				script{
                    sh 'docker-compose build web'
				}
			}
		}
		stage('Build and SonarQube Scan') {
            steps {
                script {
                    // Run SonarQube scanner
                    sh "${SONARQUBE_HOME}/bin/sonar-scanner \
                        -Dsonar.projectKey=Nodejs \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://52.91.148.253:9000 \
                        -Dsonar.login=sqa_c87013ba4b1438f886ec6d049de6dc74c0cbd1b4"
                }
            }
        }
		stage('Docker Compose'){
			steps{
				script{
                    sh 'docker-compose up web'
				}
			}
		}
	}
}
