pipeline{
	
	agent any

	stages{

		stage("checking out git"){

			steps {
            	
            	checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sangeethmohan18/gradleproject.git']]])

            	sh "echo CLONE SUCCESS"


		    }
		}

		stage(" Gradle build"){

			steps{

				sh "start/gradlew build"

				slackSend channel: 'jen-slackintegration', message: 'Build started'





			}
		}

		



	}
}
