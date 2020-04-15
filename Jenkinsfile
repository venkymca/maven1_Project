pipeline {
	agent any
	tools { 
	         maven 'Maven_Local' 
                 jdk 'Jdk_Localhost' 
      }
	stages {
		stage('---clean---'){
			steps {
				
				 bat "mvn clean"
			}
		}
		stage('---test---') {
			steps {
				
				bat "mvn test"
			}
		}
		stage('---package---'){
			steps {
				tool name: 'Maven_Local', type: 'maven'
				bat "mvn package"
			}
      post{
         archiveArtifacts artifacts: '**/*.war'
      }
		}
		
		stage('---deploy to tomcat---'){
			steps {
				  build job: 'Maven-Deployment'
			}
		}
		
		
	}
}
