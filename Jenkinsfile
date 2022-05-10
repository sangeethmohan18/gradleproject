pipeline {
	
	agent any

	stages {

		stage("checking out git"){

			steps {




				echo "######################################################################"

				echo ""
            	
            	checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sangeethmohan18/gradleproject.git']]])

            	sh "echo CLONED SUCCESSFULLY"
            }	

            
            post {
            
            	success {

            		slackSend channel: 'jen-slackintegration', message: 'Cloning completed, moving to build'

            	}
            }	


		    
		}

		stage(" Gradle build"){


			steps {

				sh "start/gradlew build"

				slackSend channel: 'jen-slackintegration', message: 'Build started'
			}	

			post {

				success{

					slackSend channel: 'jen-slackintegration', message: 'Build Successful'
				}

            	failure{

            		slackSend channel: 'jen-slackintegration', message: 'Build failed, check for logs.'
            	}

			}	

		}

				
		stage(" Archive artifact"){

			steps {

				archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false, fingerprint: true,onlyIfSuccessful: true



			}




		}



				





			
	}

		



	
}
