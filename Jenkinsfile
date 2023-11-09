pipeline{
    agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhublogin')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/Anshuman-QwikSkills/aws-devops-mini-project-6.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t anshuman123abc/notes-app .'
			}
		}
		stage('Login & Push ') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
				sh 'docker push anshuman123abc/notes-app'
				sh 'docker rmi anshuman123abc/notes-app'
			}
		}
        
    }
}
