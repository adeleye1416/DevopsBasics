
pipeline{

   agent any

	//create dockerhub credential in github with your dockerhub Username and Password/Token
	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
	
	stages {

		stage('gitclone') {

		      steps {
		         git 'https://github.com/adeleye1416/DevopsBasics.git'
		      }
		}
		
		stage('Build') {
			steps {
			
			   sh 'docker build -t adeleye1416/class_app:${BUILD_NUMBER} .'
			}
		}
		
		stage('Login') {
		
			steps {
			   sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login --username adeleye1416 --password-JahTeh!1416'    
			}
		}

		stage('Push') {
			
			steps {
			   sh 'docker push adeleye1416/class_app:${BUILD_NUMBER}'
			}
		}
		}
	
	post {
	    always {
		sh 'docker logout'
	    }
    }

}


