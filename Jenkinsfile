pipeline {
	agent{
        label 'nodejs'
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
		stage('Docker Compose'){
			steps{
				script{
                    sh 'docker-compose up web'
				}
			}
		}
	}
}
