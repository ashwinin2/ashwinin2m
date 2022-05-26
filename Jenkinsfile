pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('ashwinin2')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/ashwinin2/ashwinin2m.git'

			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t ashwinin2m/dockerfile:latest'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push ashwinin2/ashurepo_1:latest'
			}
		}
	}

	post {
		always {
			sh 'echo this is my first jenkins Pipeline'
			sh 'docker logout'
		}
	}
}
