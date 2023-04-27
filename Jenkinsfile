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
                
                sh 'sudo docker login -u $DOCKERHUB_CREDS_USR -p $DOCKERHUB_CREDS_PSW'                
                }
            }
        stage('Docker Push') {
            steps {
		//Aquí debes poner tu github
                sh 'sudo docker push ejemplodockerhub_danieladell'
                }
            }
        }
    post {
		always {
			sh 'sudo docker logout'
		}
	 }
    }

