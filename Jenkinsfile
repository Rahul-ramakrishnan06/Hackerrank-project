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
		stage('SonarQube Scan'){
			steps{
				script{
					echo "Scan.."
				}
			}
		}
		stage('Sonarqube') {
    		environment {
        		scannerHome = tool 'SonarQubeScanner'
    		}
    		steps {
        		withSonarQubeEnv('sonarqube') {
            		sh "${scannerHome}/bin/sonar-scanner"
        		}
        		timeout(time: 10, unit: 'MINUTES') {
            		waitForQualityGate abortPipeline: true
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
