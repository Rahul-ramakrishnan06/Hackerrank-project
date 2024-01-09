pipeline {
	agent{
        label 'nodejs'
	}
	stages{
		stage('Build'){
			steps{
				script{
                    sh 'sudo docker-compose build web'
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
                    echo "Scan.."
				}
			}
		}
	}
}
