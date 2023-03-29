pipeline {

        agent any
        
	environment {
	         DOCKERHUB_CREDENTIALS=credentials('gulzat-docker')
	}
        stages {

                stage('Build') {
                        steps {
                                sh 'cd awesome_cats_backend/ && docker build -t gulzatch/awesome_cats_backend:v1 -f Dockerfile .'
                                sh 'cd awesome_cats_frontend/ && docker build -t gulzatch/awesome_cats_frontend:v1 -f Dockerfile .'
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
}
