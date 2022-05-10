pipeline{
	
	agent any

	stages{

		stage("checking out git"){

			steps {
            	
            	checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sangeethmohan18/gradleproject.git']]])

            	sh "echo CLONED SUCCESSFULLY"


		    }
		}

		stage(" Gradle build"){

			steps{

				sh "cd $WORKSPACE/Gradleproject/start"

				sh "./gradlew clean build"

				slackSend channel: 'jen-slackintegration', message: 'Build started'





			}
		}

 




	}
}
