pipeline {

        agent any
        
	environment {
	         DOCKERHUB_CREDENTIALS=credentials('gulzat-docker')
	}
        stages {

                stage('Build') {
                        steps {
                                sh 'docker build -t gulzatch/awesome_cats_backend:v1 awesome_cats_backend'
                                sh 'docker build -t gulzatch/awesome_cats_frontend:v1 awesome_cats_frontend'
			 }
			 
                 }
        }

                stage('Login') {
                        steps {
 		                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
				 }
				 }
                stage('Push') {
                        steps {
                                sh 'docker push gulzatch/jenkins:myawesomecat_frontend'
	                        sh 'docker push gulzatch/jenkins:myawesomecat_backend'
                            } 
				    }
				    }