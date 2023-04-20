
pipeline {
	agent any
	
	stages{
		stage('Code'){
			steps{
				git url: 'https://github.com/mcollins1010/node-todo-cicdupdate.git', branch: 'master'
			}
		}
		stage('Build'){
			steps{
				sh 'docker build -t collinzo1010/nodeto:latest .'
			}
		}
		stage('Push'){
			steps{
				withCredentials([string(credentialsId: 'dockerHub', variable: 'dockerHubpwd')]){
				sh "docker login -u collinzo1010 -p ${dockerHubpwd}"
				sh 'docker push collinzo1010/nodeto:latest'
				}
			}
		}
			
	}

}
