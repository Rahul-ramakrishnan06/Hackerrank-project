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

        stage('Scan for Vulnerabilities') {
            steps {
                script {
                    def trivyScan = sh(script: "trivy --severity HIGH,CRITICAL ${DOCKER_IMAGE}", returnStatus: true)

                    if (trivyScan != 0) {
                        error("Vulnerabilities found in the Docker image. Build aborted.")
                    } 
                    else {
                        echo "No HIGH or CRITICAL vulnerabilities found. Proceeding with the build."
                    }
                }
            }
        }
/*		stage("Quality Gate"){
			steps{
				script{
					echo "Scan.."
					#FAILED_STAGE = env.STAGE_NAME
					#timeout(time: 5, unit: 'MINUTES') {
					#	def qg = waitForQualityGate()
					#	if (qg.status != 'OK') {
					#		error "Pipeline aborted due to quality gate failure: ${qg.status}"
						}
					}
				}
			}
		}
*/
		stage('Docker Compose'){
			steps{
				script{
                    sh 'docker-compose up web'
				}
			}
		}
	}
}
