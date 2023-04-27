pipeline {
    agent any
    environment{
        DOCKERHUB_CREDS = credentials('dockerhub')
    }
    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
                sh 'ls *'
            }
        }
        stage('Build Image') {
            steps {
                //Aquí debes poner tu github
		sh 'sudo docker build -t ejemplodockerhub_danieladell .'
            }
        }
        stage('DockerHUB Login') {
            steps {
                
                sh 'echo $DOCKERHUB_CREDS_PSW | sudo docker login -u $DOCKERHUB_CREDS_USR --password-stdin'                
                }
            }
        stage('Docker Push') {
            steps {
		//Aquí debes poner tu github
		sh 'sudo docker tag ejemplodockerhub_danieladell $DOCKERHUB_CREDS_USR/ejemplodockerhub_danieladell'
                sh 'sudo docker push $DOCKERHUB_CREDS_USR/ejemplodockerhub_danieladell'
                }
            }
        }
    post {
		always {
			sh 'sudo docker logout'
		}
	 }
    }

