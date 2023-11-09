pipeline{
    agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhublogin')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				checkout scm
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
				// sh 'docker rmi anshuman123abc/notes-app'
			}
		}
                stage("Deploy"){
                       steps {
                                echo "Deploying the container"
                                sh "kubectl apply -f k.yml"
                
            }
        }
        
    }
}
