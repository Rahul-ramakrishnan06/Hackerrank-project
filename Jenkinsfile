pipeline {
	agent{
        label 'nodejs'
	}

    environment {
        DOCKER_IMAGE = 'nodejs-multi_version-10_web:latest'
	SONARQUBE_HOME = tool 'SonarQubeScanner'
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
                        -Dsonar.host.url=http://52.91.148.253:9000
                        -Dsonar.login=sqa_8ffb79811d285200424245cfa07e74d61bd80e03"
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
