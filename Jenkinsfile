pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('Docker-hub')
	}
        
	stages {
		
		
	    stage('gitclone') {
		    
                 git 'https://github.com/akdevops12/nodejs-cicd-pipeline.git'
		stage('Build') {

			steps {
				sh 'docker build -t 30marcel/nodeapp_test:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push 30marcel/nodeapp_test:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
