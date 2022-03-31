pipeline{
    agent any 
    environment{
        VERSION = "${env.BUILD_ID}"
    }
    stages{
        stage("sonar quality check"){
            agent {
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'SONARQUBE_TOCKEN') {
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube'
                    }
		}
            }
	}
    }
}
